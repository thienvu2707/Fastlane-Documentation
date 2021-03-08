# DOCUMENTATION SETUP FASTLANE-IOS

## I - INTRODUCTION

- Fastlane is an automation app to deloy and release mobile application.

## II - PREREQUISITE

1. On all operating system on date: 04-march-2021 must have ruby environment version between 2.4 - 2.7
2.  For MacOS:
- Must installed `Xcode command line tools` newest version via terminal using code `xcode-select --install`
- (Optional) Installed Homebrew by terminal ussing code: `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
`
3. For Windows / Linux: 
- Installed Ruby environment at: `https://www.ruby-lang.org/en/downloads/` but version at this moment is between 2.4 - 2.7

## III - SETUP FASTLANE
1. Install Fastlane
- MacOS: By using Homebrew you don't need to install Ruby separately and instead homebrew installs the most adequate Ruby version for fastlane. Install fastlane via terminal: `brew install fastlane`
- Windows / Linux: Install fastlane by shells / terminal: `sudo gem install fastlane`
2. Initialize Fastlane
- First using terminal / shells to navigate to your project and run `fastlane init`
![alt](https://lh4.googleusercontent.com/c8_Dyhup7onaPXUfH3k0LBdLMwFXW2j1xwHuxNavFqdbLzlkQ8bVCg-CtauhrRrmr8qVBLsKMwIq3nwHYrPXO-kmqA8BG2Of3uDQacZ0Rh1GNWxhOjMpZ24eREGq9N58k1rlEFpz)

- Second select which automation you would like to apply to project. For example:
![alt](https://lh3.googleusercontent.com/vpZ3VXzpzMrU1H8nTk-zFeeztaYhHWLU5SFS2CXq7tWUTgos1Ayog0lD42Mrp12EgYP0xpaw0hJb1GaeVOgZ5GNuV-3mjTb91FAkTUHQOAvJH_D9fwIqWeST2YoSyBaiHbH-5mWR)

- Third Fastlane automatically ask for your Apple Developer Account if your account has multiple company or development team Fastlane will ask you to choose which one:
![alt](https://lh4.googleusercontent.com/QrV1FFE5LLc5xkGmUngCN-zf16b2Gqtm_-9cAFo2WCJaoVR9vksy6dtp_PiphcTCQKlhcty7ez0G58eMwZv_t3r5D9JG6GojCHU_JGCG3CdnJhlb5fj2z64g_lIL_gOnPGylNbE9)

- Fourth Fastlane will automatic check project bundle id with Apple Developer Portal if not match Fastlane will ask to create your project on Portal
![alt](https://lh3.googleusercontent.com/pjEJqY0znR2tmtj9zbxiwxEvpRbWKer39nNiBKSP01Ow4W3rfy95VXSoE0AGeWuT43Gb7-cUELY4dtKH6QlOGhHXu9jpMPQwPaAxu0Rcb0SKLnNTrXgI9zIBgJk381Hn4hdUZ5Mj)
- Fifth if you choose yes Fastlane will summarize what you did and ask for the name of the project on Apple Developer Portal. Afterward, it immediately
![alt](https://lh5.googleusercontent.com/olwgGuzOJMblndih86RURIT3cCiUig1OW-WfEoiAu9vnOqF4IngsGDB0UQPe0jNCU0b_LM_H_PahmZHQf5zvmxTC-XtuyA7BsZDAcA6qLoLa_kZx-xiUSyVq2g72HzntBdgKMFr_)
- Sixth Fastlane will create your project on App Store Connect and manage your metadata if you agree to it
![alt](https://lh6.googleusercontent.com/hgw3WAb-wbqCr1EzymhkvEa7pEGwmzTf_ypj1WmZHz4NI39SacDBYSVqtiX0rtr6-_VqeDGPawOIBka21EFyUPbbmXz6yVHhlQ4xlvEn0OPXHey9FaFY2V5G_njEiFs6A3ANy4Xx)

## IV - SCREENSHOT PROJECT
1. PREREQUISITE
- Project must have UITest
2. INITIALIZE FASTLANE SNAPSHOT
- In terminal type: `fastlane snapshot init`
- Fastlane will create for you a file name `SnapshotHelper.swift` in folder fastlane. Drag the folder to UITest
![alt](https://lh6.googleusercontent.com/RJqvpEHI2SYdw8usoYuOoH4Va5lWL2FqkohEVxqtvvZeZzWv0otMo-NhJlrWyCnNezJTgz1U8QaZS76QO1o_iXMo7JFmCy9GPJRGD1SL)
- In UITest file apply these code 
```
override class func setUp() {
        let app = XCUIApplication()
        setupSnapshot(app)
        app.launch()
        snapshot("1stTestView")
    }
```
- (OPTIONAL) You can change how many devices you want to take snapshot or even which languages for the project in the `Snapfile`
- In terminal type `fastlane snapshot`
- Automatically Fastlane take to screenshot of your application in multiple devices and summarize it for you
![alt](https://lh4.googleusercontent.com/8oBAdleOJGTgPB3doW-oV2GxWJDIB75_50FebjuCXI4QTrb3lFZk6Q0h7Gd7S1xtHDe8OrVZmjEpRrv66DBakayZSJ9DsQYeOjkdJie2SZSpjONc_4PpyRJFOckW3qLLgdYL_uKG)
- Then you can upload to app store connect via `fastlane deliver`
![alt](https://lh6.googleusercontent.com/xVLfTgDLG_KvxCCGYkGKhB015Vm3UfBUy9MN1WfGL-H4y4QYx0G2UTmI-DmcQhVQPhZSfNInybvPpz7aih4WGtN76rjLqQAvqe9bt98f3QJ7sNfo56TN2L8Tknjs_kpUc2QJHKi_)

## V - GETTING CERTIFICATE AND UPLOAD TO APPSTORE
1. Download `Match` a tool of fastlane to get certificate and codesigning easy to manage and share to all team member
2. Have a private repository of the project
3. Initilize match via terminal type `fastlane match init` then choose which cloud server you want to keep your certificate. For me using git
![alt](https://lh4.googleusercontent.com/f46b0g-icisJM-V_SG54d8xbxc62HGMfuDtV20VVayh7H1KeG8sdMFYhx7akBWbRtAZQXOD-EaeRhHT7poGJL34RCz3GJxwkCM1CyArTJyj1aXOWwLeR2E_1a5WRPDc5fIqw7uV-)
4. Configure Match file 
![alt](https://lh3.googleusercontent.com/uAbRsWVsFFMq8kC9Jz87NX63Ur6p0gPZdXTM7m_-8C-MLqurpQm4WW4LQh5X3a4o7RK_ayVb2jFMGNRLK9SI6kbspNqS_E0Gvk2du1bJQmhYmudjeA14Fz5IHdQtnLztAtd-jO8G)
5. Run `fastlane match appstore` to get certificate for application
![alt](https://lh3.googleusercontent.com/Ngiv1CW8xnvMl13esFbxDMgCAFmC_jJaKfJRHSeixKcbD5z6R8i54f546Gl7YucAvbfpo8Uf00AYw3fsYSyZVFIbUjIeTlICxSGcoymohq8YoEDOfR4ktTp0SND_ptBmLIBfg0xX)

___
### **However because of the limited certificate of Gumi I cannot continue after this state**
___
6. Upload to appstore `fastlane release`

## VI - REFERENCES
- https://docs.fastlane.tools
- https://docs.fastlane.tools/actions/


