# Heroku Buildpack, Chrome for Testing

This buildpack installs **Google Chrome browser** `chrome` & [`chromedriver`](https://chromedriver.chromium.org/), the Selenium driver for Chrome, in a Heroku app.

## Background

In summer 2023, the Chrome development team [addressed a long-standing problem with keeping Chrome & Chromedriver versions updated and aligned](https://developer.chrome.com/blog/chrome-for-testing/) with each other for automated testing environments. This buildpack follows this strategy to keep `chrome` & `chromedriver` versions  in-sync.

## Installation

> [!IMPORTANT]
> If migrating from a previous Chrome-chromedriver installation, then remove any pre-existing Chrome or Chromedriver buildpacks from the app.

```bash
heroku buildpacks:add -i 1 heroku-community/chrome-for-testing
```

Deploy the app to install Chrome for Testing. 🚀 

## Install Paths
The buildpack will add two files in the `/app/.chrome-for-testing` folder
- `chromedriver-linux64`
- `chrome-linux64`

## Selecting the Chrome Release Channel

By default, this buildpack will download the latest `Stable` release, which is provided
by [Google](https://googlechromelabs.github.io/chrome-for-testing/).

You can control the channel of the release by setting the `GOOGLE_CHROME_CHANNEL`
config variable to `Stable`, `Beta`, `Dev`, or `Canary`, and then deploy/build the app.

## Releasing a new version

*For buildpack maintainers only.*

1. [Create a new release](https://github.com/heroku/heroku-buildpack-chrome-for-testing/releases/new) on GitHub.
1. [Publish the release tag](https://addons-next.heroku.com/buildpacks/eb9c36ef-a265-4ea3-9468-2cd0fc3f04c1/publish) in Heroku Buildpack Registry.
