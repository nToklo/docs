![www.ntoklo.com](https://cloud.githubusercontent.com/assets/1387097/17018478/d6fa453c-4f2f-11e6-966f-40d728dd5030.png)
#Magento extension

Displays personalised product recommendations and trending product charts through integration with nToklo platform.

![Magento demo store](https://cloud.githubusercontent.com/assets/1387097/17017027/907c868e-4f29-11e6-9fcd-bd87bf6c734b.png)

######System requirements for this extension:
- Magento (Community Edition) 1.7+
- PHP 5.3+

#Features
1. Seamlessly Integrates with nToklo for retail recommendations APIs.
2. Uses the Open Data Alliance Universal Variable – Generates [Universal Variable](http://docs.qubitproducts.com/uv/intro/) JSON object and submits it to nToklo for processing to leverage user behaviour.
3. Uses native widgets to render personalised product recommendations and trending product charts through nToklo APIs.
4. Integrates with your store CMS to account for product categories.

#Installation Instructions
##Step 1: Get the extension key
Go to [Magento Connect](http://www.magentocommerce.com/magento-connect/ntoklo-recommendations.html), sign in and select your version of Magento to get a copy of the extension key.
![download plugin](https://cloud.githubusercontent.com/assets/1387097/17017026/9077e6c4-4f29-11e6-8cad-7a70b7e92223.png)

## Step 2: Install the extension on your Magento site
- From the Magento Admin menu select System > Magento Connect > Magento Connect Manager.
- Paste the extension key, from the previous step, under Install New Extensions, and “Install”.

![install plugin](https://cloud.githubusercontent.com/assets/1387097/17017025/9077365c-4f29-11e6-9b11-7399e0fcc934.png)

- The console on the bottom of the page will show the installation progress and will tell you to “Refresh” the page when finished.

## Step 3: Configuration
Return to your Magento admin. To avoid a known Magento bug, it is best you make sure you log out and then back in again to the Magento admin.

- Navigate to System > Configuration > nToklo.
- You'll need to either register with nToklo, or login with an existing account to get your Activation code in order for the extension to work.
- Choose “nToklo Registration” or “nToklo Login” and complete the simple form.
- Copy the provided Activation Code into the above field.

![config plugin](https://cloud.githubusercontent.com/assets/1387097/17017023/90681aaa-4f29-11e6-94da-03e16ceaeac7.png)

- Make sure Enabled is set to “Yes” to send the Universal Variable object to nToklo and also allow widgets to display on pages.

## Step 4: Widgets
We provide you with two sample widgets to get you started. But if you're not using the default Magento template these sample widgets will not display. You will have to create your own.

- In the Magento admin navigate to CMS > Widgets and click “Add New Widget Instance”.
- For Type select nToklo. Select the Design Package/Theme you are using. Click “Continue”.
- In “Frontend Properties” create a Widget Instance Title, this for your own reference. Choose the appropriate Store View where you want your widget to display.
- In “Layout Updates” below, click “Add Layout Update”.
- Define the pages/regions where you want your widgets to display.

You can also choose from the following two Template options:
- nToklo Column Template – Use this if your widget is in the left or right column regions, it displays a single column of results.
- nToklo Grid Template – Use this to place the widget in wider spaces like the Main Content Area, it will display the results in rows.

![frontend props](https://cloud.githubusercontent.com/assets/1387097/17017022/906830f8-4f29-11e6-85f6-e5c73cfec01d.png)

- Select the “Widget Options” tab.
- Select either Recommendations or Chart as the Widget type

**Recommendations** – This option presents personalized product recommendations in the widget. Where the user is anonymous the best option recommendations will be served. Where available, item context like the product category is used. So recommendations on product/category pages will be scoped appropriately.

**Chart** – This option is non-personalized as it provides a billboard type chart of trending products. Items in the widget are numbered numerically. Where available, item context like the product category is used. So charts on product/category pages will be scoped appropriately. You may select a Daily or Weekly chart. A week is taken as the last 7 days, i.e. it’s a rolling week.

- Header is the widget title that will be displayed on your website as the widget title.
- Widget colour can be any HEX value or HTML colour name.
- Max products is the maximum number of products the widget will display, it may be less if there is not sufficient data.
- Column count defines the number of columns displayed when using the “nToklo Grid Template” Layout from the “Frontend Properties” tab.
- Cache lifetime allows you the option to define the refresh interval, 86400 is the default.
- “Save” your configuration.

![wiget options](https://cloud.githubusercontent.com/assets/1387097/17017024/906e2df0-4f29-11e6-916e-2698ad5e5319.png)

# Customisation
For customisation directly to the recommendation's widget you can access the source code.

For styling you can access the css file: `/skin/frontend/base/default/css/ntoklo/global.css`

To change the layout of the widget you can access the template files. There are two template file:
- chart_horisontal.phtml
- chart_vertical.phtml

Path to the template files: `/app/design/base/default/template/ntoklo/recommendations/widget/`

**IMPORTANT**: Please note it will take at least 24hrs of site activity for the widget(s) to show up on your website. We cannot show you recommendations or charts until we have some user activity posted to our servers.

#View your console
Once you're all set up, you can now use the login created during your install to view recommendation analytics on your console. The [nToklo console](https://console.ntoklo.com) shows information about user activity on your store - think of it like Google Analytics, with a retail focus. You can:

- See a snapshot of all activity on your site on the *clickthroughs* tab. How busy are you today / this week / this month?
- See how well your recommendations are converting on the *conversions* tab.
- Find out what the best performing location for recommendations is and reposition them if necessary.
- View your purchase funnel on the *item activity* tab, where user browsing history is broken down for you into events such as browse, preview and purchase.
- See which times of the day, week and month are the busiest on the *user activity* tab.
- See summary figures for today, this week and this month, in relation to the average, busiest and quietest days / weeks / months on on all four tabs.
- Keep track of real-world events such as promotional campaigns, overlaying the data on the graphs using our annotations.
- We've packed a ton of features into this console but still kept it easy-to-use, so why not [take a look](https://console.ntoklo.com)? Please note that you'll need an up-to-date browser, such as Chrome, Safari or Firefox (or IE10).