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
* [Setting Up Your Authentication](#setting-up-your-authentication)
* [Upload Your Application](#upload-your-application)
* [Run Your First Test](#run-your-first-test)
* [Executing The Tests](#executing-the-tests)
* [Troubleshooting](#troubleshooting)
* [About LambdaTest](#about-lambdatest)

---

## Pre-requisites

Before you can start performing Ruby automation testing with Appium, you would need to:

1. **Install Ruby**: Ensure you have Ruby 3.4+ installed.
   - For **Windows**, download from [RubyInstaller](https://rubyinstaller.org/downloads/).
   - For **macOS**, run `brew install ruby`.

2. **Clone The Sample Project**:
   ```bash
   git clone [https://github.com/Priya2224/LT-appium-ruby.git](https://github.com/Priya2224/LT-appium-ruby.git)
   cd LT-appium-ruby


Setting Up Your Authentication
Make sure you have your LambdaTest credentials with you to run test automation scripts. To obtain your access credentials, purchase a plan or access the Automation Dashboard.

Set LambdaTest Username and Access Key in environment variables.

For Linux/macOS:
export LT_USERNAME=YOUR_LAMBDATEST_USERNAME \
export LT_ACCESS_KEY=YOUR_LAMBDATEST_ACCESS_KEY

For Windows:
set LT_USERNAME=YOUR_LAMBDATEST_USERNAME
set LT_ACCESS_KEY=YOUR_LAMBDATEST_ACCESS_KEY


Upload Your Application
Upload your iOS application (.ipa file) or android application (.apk file) to the LambdaTest servers using our REST API.

Using App File:

For Linux/macOS:
curl -u "YOUR_LAMBDATEST_USERNAME:YOUR_LAMBDATEST_ACCESS_KEY" \
--location --request POST '[https://manual-api.lambdatest.com/app/upload/realDevice](https://manual-api.lambdatest.com/app/upload/realDevice)' \
--form 'name="Android_App"' \
--form 'appFile=@"/Users/macuser/Downloads/proverbial_android.apk"'

For Windows:
curl -u "YOUR_LAMBDATEST_USERNAME:YOUR_LAMBDATEST_ACCESS_KEY" -X POST "[https://manual-api.lambdatest.com/app/upload/realDevice](https://manual-api.lambdatest.com/app/upload/realDevice)" -F "appFile=@"/Users/macuser/Downloads/proverbial_android.apk""

Using App URL:

For Linux/macOS:
curl -u "YOUR_LAMBDATEST_USERNAME:YOUR_LAMBDATEST_ACCESS_KEY" \
--location --request POST '[https://manual-api.lambdatest.com/app/upload/realDevice](https://manual-api.lambdatest.com/app/upload/realDevice)' \
--form 'name="Android_App"' \
--form 'url="[https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk](https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk)"'

For Windows:
curl -u "YOUR_LAMBDATEST_USERNAME:YOUR_LAMBDATEST_ACCESS_KEY" -X POST "[https://manual-api.lambdatest.com/app/upload/realDevice](https://manual-api.lambdatest.com/app/upload/realDevice)" -d "{"url":"[https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk](https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk)","name":"sample.apk"}"

Tip: If you do not have an app file, use our sample Android app or iOS app. The response will be a JSON object containing the App URL (e.g., lt://APP12345).


Run Your First Test
Configuring Your Test Capabilities
Update your custom capabilities in your test scripts (android-sample.rb or ios-sample.rb). For Ruby 3.4, you must use Symbols for keys in the driver initialization.

Android Config Example:
caps = {
  "lt:options" => {
    :deviceName => "Galaxy S21",
    :platformName => "Android",
    :platformVersion => "11",
    :build => "Ruby Vanilla - Android",
    :name => "Ruby Android Test",
    :isRealMobile => true,
    :app => "YOUR_APP_URL", # Enter lt:// APP URL here
    :w3c => true
  },
  :platformName => "Android"
}


iOS (.ipa) Configuration:
caps = {
  "lt:options" => {
    :deviceName => "iPhone 13 Pro",
    :platformName => "iOS",
    :platformVersion => "15",
    :build => "Ruby Vanilla - iOS",
    :name => "Ruby iOS Test",
    :isRealMobile => true,
    :app => "YOUR_APP_URL", # Enter lt:// APP URL here
    :w3c => true
  },
  :platformName => "iOS"
}


Executing The Tests

1. Install required gems:
bundle install

2. Run Android Test:
ruby android-sample.rb

3. Run iOS Test:
ruby ios-sample.rb


Troubleshooting
Ruby 3.4 ArgumentError
If you encounter ArgumentError (String cannot be converted to Symbol), ensure you initialize your driver with symbols for the main keys:

@appium_driver = Appium::Driver.new({
  :caps => caps,
  :appium_lib => { :server_url => "https://#{username}:#{accessToken}@[mobile-hub.lambdatest.com/wd/hub](https://mobile-hub.lambdatest.com/wd/hub)" }
}, true)


About LambdaTest
LambdaTest is a leading test execution and orchestration platform. It allows users to run both manual and automated testing of web and mobile apps across 3000+ different browsers, operating systems, and real device combinations.

Features
Run Appium, Selenium, and Playwright automation tests across 3000+ real environments.

Real device cloud for both Android and iOS.

Blazing fast test automation with HyperExecute.

120+ third-party integrations with CI/CD tools.

We are here to help you 🎧
Got a query? We are available 24x7. Contact Us

Visit LambdaTest for more info.

<img height="53" width="200" src="https://user-images.githubusercontent.com/70570645/171866795-52c11b49-0728-4229-b073-4b704209ddde.png">

