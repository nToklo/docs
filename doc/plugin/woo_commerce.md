![www.ntoklo.com](https://cloud.githubusercontent.com/assets/1387097/17018478/d6fa453c-4f2f-11e6-966f-40d728dd5030.png)
# WooCommerce plugin

Recommendations for WooCommerce allows users of the WordPress e-Commerce platform, who use the WooCommerce toolkit, to easily place recommendations and charts on their stores. The widgets have a range of layouts and colour schemes and all API integration is handled behind-the-scenes, making it quick and easy to set up.

![woo plugin](https://cloud.githubusercontent.com/assets/1387097/17017021/9067e526-4f29-11e6-8ce1-c070226edd5c.png)

## Features
1. Free – no catch (well, nearly) nToklo’s service is free for up to 100,000 events per day. If you’ve got more than that much activity on your site, you really should call us and found out how much more we can do for enterprise customers.

2. Get insight into your customers Our analytics console for your nToklo account shows user activity, best-performing recommendation location, purchase funnel and busiest times of day / week / month

3. Quick & easy to setup Plugin installation is quick and easy – you can create your (required) nToklo account without leaving your WordPress admin panel.

4. Quick start with built-in widget styles & colour schemes The plugin comes with 8 layouts and 6 colour schemes to integrate the widgets with the look and layout of your site.

5. No technical knowledge required Well, no more than knowing your way around the WooCommerce admin panel. Recommendations or charts can be displayed on your site easily with widgets, but if you know your way around WordPress templates, you can place recommendations and charts anywhere on your site with small changes to a few files.

###### System requirements
- WordPress 3.5+
- PHP 5.3+

##Installation instructions

### Step 1: Install our plugin
You can install nToklo via the Plugins > Add New menu item in your WordPress admin. Search for nToklo or download woocommerce-recommendations.zip from the WordPress plugin directory then click on the Upload tab.

### Step 2: Create your nToklo account
- Once the plugin is installed and activated, you should be redirected to the Settings tab at Woocommerce > nToklo Recommendations.
- If this is your first time setting up nToklo, click the “I don't have an nToklo account” button. If you do already have an account, log in through “I already have an nToklo account”.
- Fill in the simple form, a couple of the form fields are pre-populated for you.
- Once you click “Register” and the form has successfully submitted, your app is created. Now you just need to copy the code from the panel on the right into the panel on the left, then “Save Changes”.

![create account](https://cloud.githubusercontent.com/assets/1387097/17017020/90675e9e-4f29-11e6-82b4-12ef374a00d9.png)

### Step 3: Place widgets on your site
- The easiest way to place widgets on your pages is via the admin under Appearance > Widgets. You should have 2 new Available widgets called ‘WP e-Commerce Chart’ and ‘WP e-Commerce Recommendations’.
- Add the required widget(s) into the desired location, change the title and settings as required.

![place wigets](https://cloud.githubusercontent.com/assets/1387097/17017019/9066a47c-4f29-11e6-8adf-0cf46f61acbb.png)

- Alternatively, you can paste shortcode like the following into your pages:
```php
[ntoklo_chart title="Top 10" max_items=10 widget_color=dark_blue]
[ntoklo_recommendations title="We recommend" layout=grid_2_column widget_color=blue max_items=4]
```

- Or if required, shortcode like the following straight into your template:
```php
<?php echo do_shortcode( '[ntoklo_recommendations title=
    "We recommend for you" layout=grid_4_column widget_color=orange max_items=4]' ); ?>
```


**IMPORTANT**: Please note it will take at least 24hrs of site activity for the widget(s) to show up on your website. We cannot show you recommendations or charts until we have some user activity posted to our servers.

## View your console
Once you're all set up, you can now use the login created during your install to view recommendation analytics on your console. The [nToklo console](https://console.ntoklo.com) shows information about user activity on your store - think of it like Google Analytics, with a retail focus. You can:

- See a snapshot of all activity on your site on the *clickthroughs* tab. How busy are you today / this week / this month?
- See how well your recommendations are converting on the *conversions* tab.
- Find out what the best performing location for recommendations is and reposition them if necessary.
- View your purchase funnel on the *item activity* tab, where user browsing history is broken down for you into events such as browse, preview and purchase.
- See which times of the day, week and month are the busiest on the *user activity* tab.
- See summary figures for today, this week and this month, in relation to the average, busiest and quietest days / weeks / months on on all four tabs.
- Keep track of real-world events such as promotional campaigns, overlaying the data on the graphs using our annotations.
- We've packed a ton of features into this console but still kept it easy-to-use, so why not [take a look](https://console.ntoklo.com)? Please note that you'll need an up-to-date browser, such as Chrome, Safari or Firefox (or IE10).