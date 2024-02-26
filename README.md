# Webview-Modal-Survey

## About
This macro serves as an example of how you can open up a WebView Modal on the Cisco Room Navigator.

Great starting point when first working with Webview Display APIs.

## Features

* Automatic UI Generation
* WebView Target Detection
  * Determines whether to show on the OSD or Navigator based on available resources
* OSD User Tool Tips
* Simple Configuration
* Cache Handling

## Installation
* Download a copy of the webview-modal-automated-prompt.js Macro
* Login into the Web Interface of your Device
* Enable CommonProxy in Configuration->NetworkServices
* Navigate to the Macro Editor
* Select Import from file, and add the webview-modal-automated-prompt.js file
* Alter the config object of the Macro
* Save the Macro
* Activate the Macro

## Use Cases
* Post Meeting Surveys
* Service Ticket Portal
* Ordering Coffee

## Configuration
The webview-modal-automated-prompt.js macro has an object near the top of the script. You can change a few items on the fly to alter the Macro user experience. To the right of each nested object is a list of accepted values and a description of each Value.

## CodeView
```
const config = {
  WebModal: { // Set Values pertaining to a Web Based Modal
    Title: 'Survey',                     //Set a user facing title for the Web Modal
    Url: 'https://cisco.com',           // Set the URL you want to open
    OSDToolTip: {                       // If the modal is prompted by a trigger without user interaction, this tooltip will show to help guide the user
      Mode: true,
      Message: 'Tell us about your experience on the Touch Panel 🙂',
      Duration: 15,
      Location: 'Top-Right', // Top-Right, Top-Left, Center, Bottom-Right, Bottom-Left
    },
    Triggers: { // Choose how the WebModal should be prompted to open
      PanelClicked: true,               // If true, will generate a user facing panel to open the WebModal when clicked
      CallDisconnect: true              // If true, the WebModal will open when a call disonnects
    },
    ClearCacheOnExit: {
      Mode: true,                      // If true, it will clear cache for Webapps
      Target: 'WebApps'                 // All, Signage, WebApps, PersistentWebApp
    },
    WebViewTimoutDuration: { // Choose how long the Survey Form stays on screen
      Mode: true,             // If true, it will close Webview Panel after duration timer
      Duration: 18             //Number of seconds 
    }
  },
  UserInterface: {
    Panel: {
      Name: 'Survey',     // Set the Name of the WebApps Panel
      Location: 'HomeScreen',           // HomeScreen, HomeScreenAndCallControls, CallControls, Never, ControlPanel
      Order: 1,                         // Set the Position where this panel will render amongst other Custom Panels. Does not effect Native Panels
      Icon: {
        Type: 'Blinds',                 // Choose an Option from the list Below. Note, Custom expect a the CustomIconURL to be provided
        /*
        "Blinds", "Briefing", "Camera", "Concierge", 
        "Custom", "Disc", "Handset", "Help", "Helpdesk", 
        "Home", "Hvac", "Info", "Input", "Language", 
        "Laptop", "Lightbulb", "Media", "Microphone", 
        "Power", "Proximity", "Record", "Sliders", "Tv"
        */
        Color: 'cf7900',                // Set a Background Color using a Hexadecimal Value. Does not apply to Custom Icons or Icons located in the Control Panel
        CustomIconURL: 'https://avatars.githubusercontent.com/u/159071680?s=200&v=4' // Must be a .ico, .jpg or .png file that's between 60x60px to 1200x1200px in size. If the image fails to download, the icon above will be used
      }
    }
  }
}
```
