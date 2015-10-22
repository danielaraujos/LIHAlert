# LIHAlert
LIHAlert provides animated banners for iOS which is written using the apple's newest programming language Swift 2.0. 

### Requirements
Xcode 7+

###Usage

####1. Predefined Banners
* Text banner
* Text with an ActivityIndicator
* Text with an icon
* Text with a button
* Text with two buttons
* Custom view banner
* 
LIHAlert contains some predefined alerts for each Alert type. You can use following code snippets to use them. 

#####Text Banner
<img src="http://3.bp.blogspot.com/-LLVpn6KrnNg/ViiaKmCHIqI/AAAAAAAACsw/13dVIUMG7E0/s300/TextBanner.gif" />

```Swift
    var textAlert: LIHAlert?

    override func viewDidLoad() {
        super.viewDidLoad()
        self.textAlert = LIHAlertManager.getTextAlert("Sample Message")
        self.textAlert?.initAlert(self.view)
    }
    func showBanner(sender: AnyObject) {
        self.textAlert?.show(nil, hidden: nil)
    }
```
Call showBanner() function to show the banner


#####Success Alert
<img src="http://2.bp.blogspot.com/-pMF5l-2VR0c/ViiaJ8bohOI/AAAAAAAACss/qFciyfThVUg/s300/Success.gif" />

```Swift
    var successAlert = LIHAlertManager.getSuccessAlert("Successfully subscribed")
```

To change the icon,
```Swift
    successAlert?.icon = UIImage(named:"imageName")
```

#####Error Alert
<img src="http://2.bp.blogspot.com/-UgMys4O6Jg8/ViiaJ88bTfI/AAAAAAAACsk/qqw1_bSHkpY/s300/Error.gif" />

```Swift
    var LIHAlertManager.getErrorAlert("Failed. Please try again")
```

#####Processing Alert

This is a banner with a text and an activity indicator. This is not an auto close banner. You have to hide it when the process is finished.
<img src="http://3.bp.blogspot.com/-ASkTzpFIuSU/ViiaK2_mSYI/AAAAAAAACs8/6stjXecZWqI/s300/TextWithLoading.gif" />

```Swift
    var processingAlert: LIHAlert?

    override func viewDidLoad() {
        super.viewDidLoad()
        self.processingAlert = LIHAlertManager.getProcessingAlert("Fetching data...")
        self.processingAlert?.initAlert(self.view)
    }
    func showBanner(sender: AnyObject) {
        self.processingAlert?.show(nil, hidden: nil)
    }
    
    override hideBanner(sender: AnyObject) {
        self.processingAlert?.hide(nil)
    }
```
Call showBanner() function to show the banner and hideBanner() to hide the banner.
To change the activity indicator style,
```Swift
    processingAlert?.activityIndicatorStyle = UIActivityIndicatorViewStyle.WhiteLarge
```

#####Text with a button Alert
This alert contains a button along with a text. More suitable for notifying important messages to user.
<img src="http://2.bp.blogspot.com/-lrD_IGv93yE/ViiaKyqoRVI/AAAAAAAACs4/ggqDlP9E-YY/s300/TextWithButton.gif" />

```Swift
    var textWithButtonAlert: LIHAlert?

    override func viewDidLoad() {
        super.viewDidLoad()
        self.textWithButtonAlert = LIHAlertManager.getTextWithButtonAlert("You have successfully subscribed for the monthly newsletter", buttonText: "Dismiss")
        self.textWithButtonAlert?.initAlert(self.view)
    }
    func showBanner(sender: AnyObject) {
        textWithButtonAlert?.show(nil, hidden: nil)
    }
```
Call showBanner() function to show the banner. 
Implement your view controller from LIHAlertDelegate.

```Swift
class ViewController: LIHAlertDelegate {

    func buttonPressed(button: UIButton) {
        print(“You have pressed the button”)
        self.textWithButtonAlert?.hideAlert(nil)
    }
}
```

#####Text with two buttons Alert
This alert contains two buttons along with a text.
<img src="http://3.bp.blogspot.com/-1pXYpVNoNz0/ViiaLcHSqnI/AAAAAAAACtI/NQjV1Pe9ACs/s300/TextWithTwoButtons.gif" />

```Swift
    var textWithTwoButtonsAlert: LIHAlert?

    override func viewDidLoad() {
        super.viewDidLoad()
        self.textWithTwoButtonsAlert = LIHAlertManager.getTextWithTwoButtonsAlert("Do you want to subscribe for the monthly newsletter?", buttonOneText: "Subscribe", buttonTwoText: "Cancel")
        self.textWithTwoButtonsAlert?.initAlert(self.view)
    }
    func showBanner(sender: AnyObject) {
        textWithTwoButtonsAlert?.show(nil, hidden: nil)
    }
```
Call showBanner() function to show the banner. 
Implement your view controller from LIHAlertDelegate.

```Swift
class ViewController: LIHAlertDelegate {
    func buttonOnePressed(button: UIButton) {
        self.textWithTwoButtonsAlert?.hideAlert({ () -> () in
            self.successAlert?.show(nil, hidden: nil)
        })
        
    }
    func buttonTwoPressed(button: UIButton) {
        self.textWithTwoButtonsAlert?.hideAlert(nil)
    }
}
```


#####Custom View Alert
You can specify any view to act as the banner.
<img src="http://4.bp.blogspot.com/-lHReuTyaJ8A/ViiaJyAiEfI/AAAAAAAACso/Q9A-X3MNcTo/s1600/CustomView.gif" />

```Swift
    var customViewAlert: LIHAlert?

    override func viewDidLoad() {
        super.viewDidLoad()
	//In this case I am using an ImageView as the banner
        let customView = UIImageView(frame: CGRectMake(0.0, 64.0, 100, 50))
        customView.image = UIImage(named: "customViewImage")
        self.customViewAlert = LIHAlertManager.getCustomViewAlert(customView)
        self.customViewAlert?.initAlert(self.view)

    }
    func showBanner(sender: AnyObject) {
        self.customViewAlert?.show(nil, hidden: nil)
    }
```

####2. Create a banner

