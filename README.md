# Ruby With Appium ![pw](https://img.shields.io/badge/Ruby-CC342D?style=for-the-badge&logo=ruby&logoColor=white)

<p align="center">
<img height="500" src="https://user-images.githubusercontent.com/95698164/171857146-90e52e22-0070-4798-b2a5-6cc525a4da66.png">
</p>

<p align="center">
  <a href="https://www.lambdatest.com/blog/?utm_source=github&utm_medium=repo&utm_campaign=LT-appium-ruby" target="_bank">Blog</a>
  &nbsp; &#8901; &nbsp;
  <a href="https://www.lambdatest.com/support/docs/?utm_source=github&utm_medium=repo&utm_campaign=LT-appium-ruby" target="_bank">Docs</a>
  &nbsp; &#8901; &nbsp;
  <a href="https://www.lambdatest.com/learning-hub/?utm_source=github&utm_medium=repo&utm_campaign=LT-appium-ruby" target="_bank">Learning Hub</a>
  &nbsp; &#8901; &nbsp;
  <a href="https://www.lambdatest.com/newsletter/?utm_source=github&utm_medium=repo&utm_campaign=LT-appium-ruby" target="_bank">Newsletter</a>
  &nbsp; &#8901; &nbsp;
  <a href="https://www.lambdatest.com/certifications/?utm_source=github&utm_medium=repo&utm_campaign=LT-appium-ruby" target="_bank">Certifications</a>
  &nbsp; &#8901; &nbsp;
  <a href="https://www.youtube.com/c/LambdaTest" target="_bank">YouTube</a>
</p>

*Appium is a tool for automating native, mobile web, and hybrid applications on iOS, Android, and Windows platforms. Perform Appium automation tests on [LambdaTest's online cloud](https://www.lambdatest.com/appium-mobile-testing).*

[<img height="53" width="200" src="https://user-images.githubusercontent.com/70570645/171866795-52c11b49-0728-4229-b073-4b704209ddde.png">](https://accounts.lambdatest.com/register)

## Table of Contents

* [Pre-requisites](#pre-requisites)
* [Run Your First Test](#run-your-first-test)
* [Executing The Tests](#executing-the-tests)
* [Troubleshooting](#troubleshooting)

## Pre-requisites

Before you can start performing Ruby automation testing with Appium, you would need to:

- Install **Ruby** on your local system (Ruby 3.4+ recommended).
- For **Windows**, download from [rubyinstaller.org](https://rubyinstaller.org/downloads/).

### Clone The Sample Project

```bash
git clone [https://github.com/Priya2224/LT-appium-ruby.git](https://github.com/Priya2224/LT-appium-ruby.git)
cd LT-appium-ruby

Setting Up Your Authentication
Set LambdaTest Username and Access Key in your environment variables.

For Windows:

set LT_USERNAME=YOUR_LAMBDATEST_USERNAME
set LT_ACCESS_KEY=YOUR_LAMBDATEST_ACCESS_KEY

Upload Your Application
Upload your app via cURL to get your lt:// App URL.

For Windows:

curl -u "USER:KEY" -X POST "[https://manual-api.lambdatest.com/app/upload/realDevice](https://manual-api.lambdatest.com/app/upload/realDevice)" -F "appFile=@"C:/path/to/your/app.apk""Run 

Your First Test
Configuring Your Test Capabilities (W3C & Ruby 3.4 Fix)
To prevent ArgumentError in Ruby 3.4, your Appium::Driver.new call must use Symbols for keys.

Android Configuration:

Ruby
caps = {
    "lt:options" => {
        :deviceName => "Pixel 6",
        :platformName => "Android",
        :platformVersion => "13",
        :build => "Ruby Vanilla - Android",
        :name => "Ruby Android Test",
        :isRealMobile => true,
        :app => "YOUR_APP_URL",
        :w3c => true
    },
    :platformName => "Android"
}

Executing The Tests
Navigate to your folder and run the script using bundle exec to ensure the correct environment.

Run Android Test:

Bash
bundle exec ruby android-sample.rb
Run iOS Test:

Bash
bundle exec ruby ios-sample.rb
Troubleshooting
"ArgumentError: String cannot be converted to Symbol"
This is a Ruby 3.4 specific fix. Ensure your driver is initialized like this:

Ruby
# The fix: Using :caps and :appium_lib as symbols
appium_driver = Appium::Driver.new({
    :caps => caps,
    :appium_lib => {
        :server_url => "https://#{username}:#{accessToken}@[mobile-hub.lambdatest.com/wd/hub](https://mobile-hub.lambdatest.com/wd/hub)"
    }}, true)
Gem Conflicts
If you encounter No such file or directory or version mismatches:

Delete Gemfile.lock.

Run bundle update.

Run bundle install.

About LambdaTest
LambdaTest is a leading test execution platform. It allows users to run manual and automated testing across 3000+ different browsers and real devices.

<img height="53" width="200" src="https://user-images.githubusercontent.com/70570645/171866795-52c11b49-0728-4229-b073-4b704209ddde.png">