# selenium-driver-binaries

Maven dependencies for binaries needed by [Selenium](http://www.seleniumhq.org/) for certain browsers

## What is it?

Some browsers require an external, binary file to help Selenium connect. For example, in order to use [Google Chrome](http://www.google.com/chrome/) on Windows, **chromedriver.exe** must be present.

The purpose of this project is to make these binaries available as a maven dependency, so that, instead of having to include them as part of your project, you can simply use maven to download them automatically.
