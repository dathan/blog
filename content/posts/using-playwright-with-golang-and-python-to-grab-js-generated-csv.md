---
title: "Using Playwright With Golang and Python to Grab Js Generated Csv"
date: 2023-04-25T16:10:17-07:00
draft: false
---
# Problem

I am helping out a friend, to process reports which are behind a paywall and store them in a database to create a churn detector, which will enable his crew to address the churn at hand.


## Details

What is churn? Churn is a term used by companies to denote that a customer no longer wants to use the services they previously paid for. Each company has different metrics to give an indication that a customer is CHURING. The churn for my friend is, customers are not ordering new products which they ordered in the past and the amount they ordered is definitely consumed.

## Environment

The data is stored on a report website that is behind a subscription, requiring a username and password. The API that the report site uses, passes HTML as POST arguments to their backend, and the backend may error out. The HTML dom that is selected is from JQUERY. I am assuming that the backend is parsing the form passed for some reason instead of the values, thus the need to send HTML blocks. I am very biased when it comes to sending messages between systems, and instead of finding out why, I am working around the issue using Playwright to grab the results of this system for me.

## Playwright 

Playwright is probably the best e2e testing tool that I came across. All major browsers are supported and this fact/feature allows developers to run automated tests that the sight will work, and what is expected like say logging in works across browsers. It can also be used to grab generated data and be used as a crawler, this is how I am using it.

First I started with Python, the reason is I wanted to use the following command 

`playwright codegen <url>`

this command starts up a Chrome browser to a URL and will record the user actions to generate the Python code to replay again. This feature is not supported in Golang for the community version called `playwright-go`. My report parser is written in Go, so fetching the data with Go and processing it is desirable. I do not want to write the actual code gen code I want tools to do it for me. Thus the approach.


In reality, I had to end up translating and editing but that was quick, the code gen got me far. Inside my pkg directory, I am using domains, the crawler domain contains the following code.

```go

type Crawler struct {
	FilesSaved        []string
	ReportsToDownload []string
}

func NewCrawler(reports []string) *Crawler {

	return &Crawler{
		FilesSaved:        []string{},
		ReportsToDownload: reports,
	}
}

func (c *Crawler) DownloadReports() (*Crawler, error) {
	pw, err := playwright.Run()
	if err != nil {
		return c, err
	}

	browser, err := pw.Chromium.Launch(playwright.BrowserTypeLaunchOptions{Headless: playwright.Bool(false), Channel: playwright.String("chrome")})
	if err != nil {
		return c, err
	}

	context, err := browser.NewContext()
	if err != nil {
		return c, err
	}

	page, err := context.NewPage()
	if err != nil {
		return c, err
	}

	if _, err = page.Goto("https://reports.example.com"); err != nil {
		return c, err
	}

	emailLocator, err := page.Locator(`input[placeholder="someone@example.com"]`)
	if err != nil {
		return c, err
	}

	emailLocator.Click()
	emailLocator.Fill("dathan@example.com")
	emailLocator.Press("Enter")

	passwordLocator, err := page.Locator(`input[placeholder="Password"]`)
	if err != nil {
		return c, err
	}

	passwordLocator.Click()
	passwordLocator.Fill(os.Getenv("REPORT_PASSWORD"))

	signInButton, err := page.Locator(`#submitButton`)
	if err != nil {
		return c, err
	}

	err = signInButton.Click()
	if err != nil {
		return c, err
	}


```



### Explain

The code above is an example of launching a chrome browser in incognito mode, a new context is created, a new page is created for that context, that page is navigated to `reports.example.com` and a username and password field is clicks on, and filled with my data. Once the login happens, there is more code that will download the report, which is not listed.


### Everything works.

What took data teams 6 hours to do, this program does it in a few minutes. Time is saved and the team can sell faster, which means more money. Solving real probems that has a tangle return.


## Resources

- https://playwright.dev/docs/browsers
- https://playwright.dev/docs/codegen#:~:text=Record%20a%20New%20Test%E2%80%8B&text=In%20the%20browser%20go%20to,or%20close%20the%20browser%20window.
- https://github.com/playwright-community/playwright-go



