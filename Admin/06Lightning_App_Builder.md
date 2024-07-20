# What is Lightning App Builder?

The *Lightning App Builder* is a point-and-click tool that makes it easy to create custom pages for the Salesforce mobile app and Lightning Experience, giving your users what they need all in one place. A *Lightning page* is a custom layout that lets you design pages for use in the Salesforce mobile app or Lightning Experience. A Lightning page is composed of *regions* that contain components.
A *Lightning component* is a compact, configurable, and reusable element that you can add to a Lightning page in the Lightning App Builder.

Lightning pages support these components:

- **Standard Components** - Standard components are Lightning components built by Salesforce.
- **Custom Components** - Custom components are Lightning components that you or someone else have created. You can configure custom Lightning components to work in Lightning App Builder.
- **Third-Party Components on AppExchange** - The AppExchange provides a marketplace for Lightning components. You can find packages containing components already configured and ready to use in the Lightning App Builder.

**With the Lightning App Builder, you can build:**

- Single-page apps that drill down into standard pages
- Dashboard-style apps, such as apps to track top sales prospects or key leads for the quarter
- “Point” apps to solve a particular task, such as an expense app for users to enter expenses and monitor expenses they’ve submitted
- Custom record pages for your objects, tailored to the needs of your users
- Custom Home pages containing the components and features that your users use most

**Lightning App UI**
1. **Header** - shows you its label, and contains a Pages list where you can see the last 10 pages that you modified, also shows the app name and contains an App Settings tab where you can configure the app’s options such as branding, navigation, and the utility bar. In an app context, the Pages list shows all active Lightning pages associated with the current app.
2. **Toolbar**- Use the buttons in the toolbar to cut Cut, copy Copy, and paste Paste page content; and to undo Undo, redo Redo, save, or activate your Lightning page. You can also view your page in different formats, refresh the canvas, or adjust the canvas size to fit your view.
3. **Component Palette**- contains all standard and custom Lightning components that are supported for your Lightning page
4. **Lightning Page Canvas**- area to build your page
5. **Properties Pane** - shows either the overall page properties or the properties of the component that you’ve selected

**Lightning Page Types**:

1. **App Page** - Use an app page to create a home page for a third-party app that you can add directly into the Salesforce mobile app and Lightning Experience navigation menus. 
2. **Home Page** - Create Home pages with features relevant to specific types of users, and assign the customized pages to different apps or app-and-user-profile combinations. 
3. **Record Page** - you can create a customized version of an object’s record page, tailoring it to your users’ needs. Custom record pages are supported in Lightning Experience and in the Salesforce mobile app. 

# Dynamic Forms

Dynamic Forms takes the Lightning App Builder to a whole new level. It lets you, the Salesforce admin, build highly flexible and dynamic experiences your users will love by configuring record detail fields and sections inside the Lightning App Builder.

**Dynamic Forms gives you:**

**An instant upgrade from page layouts**: Place fields and sections wherever you want.
**Dynamic layouts**: Use visibility rules to show and hide fields and sections.
**Simpler layout management**: 
    Manage the fields and sections on your pages in the Lightning App Builder without touching the page layout editor.
    Reduce the number of page layouts and record types you need by defining component visibility rules.
    Assign a Lightning page without having to assign a page layout too.

**How Does Dynamic Forms Work?**

Dynamic Forms adds a new tab to the component pane: Fields. The Fields tab contains the Field Section component and a list of fields. You can put a Field Section component anywhere on the page, and you can put fields anywhere within a Field Section component.

**You can start using Dynamic Forms in two ways:**

- Create a fresh Lightning record page. Then, click the Fields tab in the Lightning App Builder component pane, and start dragging sections and fields anywhere you want them on the page.
- Open an existing record page and with just a few clicks, migrate its record details using the Dynamic Forms migration wizard.