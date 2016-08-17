# FrontFundr Campaign Widget

The widget return all current live FrontFundr campaigns in a random order. The widget will resize to match the width and height of the container DOM object. It's recommended that the widget be put inside a `<div></div>` with the width and height specified to your sites needs.

**Widget Code**
```javascript
<!-- FrontFundr Campigns Widget Start -->
<script src="https://www.frontfundr.com/Scripts/iframeResizer.min.js"></script>
<style> iframe { width: 100%; } </style>
<iframe id="ffCampaignWidgetFrame" scrolling="no"></iframe>
<script>
    // id of specific campaign
    var id = ""; // example: "45"

    // max number of campigns to return
    var max = ""; // example: "3"

    // id takes precedence over max

    document.getElementById("ffCampaignWidgetFrame").src = "https://www.frontfundr.com/Content/Widgets/CampaignWidget.html?id=" + id + "&max=" + max;
</script>
<script>iFrameResize({log:false})</script>
<!-- FrontFundr Campigns Widget End -->
```

**Demo**

[https://www.frontfundr.com/Content/Widgets/CampaignWidgetExample.html](https://www.frontfundr.com/Content/Widgets/CampaignWidgetExample.html)

##Parameters
There are two optional parameters: `id` and `max`.

**Id** is the unique campaign id and can be found by querying the API from within your browser: 'https://www.frontfundr.com/api/campaign'. Id takes precedence over max. To alter the id param edit this line within the widget:

`var id = ""; // example: "45"` becomes: `var id = "45"; // example: "45"`

**Max** is the maximum number of results to return. To alther the max param edit this line within the widget:

`var max = ""; // example: "3"` becomes: `var max = "3"; // example: "3"`


---

# FrontFundr Campaign Api

Returns all relevant data for current live campaigns in a random order.

**Base URLs for API**

`https://www.frontfundr.com/api/campaign/<id>'

`https://www.frontfundr.com/api/campaign/getwithmax/<max>'

##Parameters

The `id` and `max` parameters are optional. The id param allows you to return a specific campaign. The max param allows you to define a count or maximum amount of campaigns to return.

**Example 1 - Specific Campaign**

`https://www.frontfundr.com/api/campaign/45`

Result:

```
{  
   "Id":"45",
   "ImageSrc":"www.frontfundr.com/Content/Upload/company_1285_HitchPlanet_New_FMT.jpg_20160722160833045.jpg",
   "Title":"HitchPlanet",
   "TargetRaise":"$250,000",
   "EquityOffered":"12 %",
   "MinInvestment":"$500",
   "ClosingDay":"11/4/2016",
   "PercentRaised":"2%",
   "Description":"HitchPlanet aims to democratize travel between cities by using technology to help people share rides in cars, creating a more social, affordable and sustainable intercity transport system for all."
}
```

**Example 1 - Two Campaigns**

`https://www.frontfundr.com/api/campaign/getwithmax/2`

Result:

```
[  
   {  
      "Id":"24",
      "ImageSrc":"www.frontfundr.com/Content/Upload/company_1169_Resized Logo.png_20151127005249815.png",
      "Title":"The Networking Effect",
      "TargetRaise":"$450,000",
      "EquityOffered":"22 %",
      "MinInvestment":"$25,000",
      "ClosingDay":"8/31/2016",
      "PercentRaised":"47%",
      "Description":"Our Vision is to connect small business people in an online community to help each realize their potential, providing the step-by-step process to maximize efficiency with their networking efforts."
   },
   {  
      "Id":"41",
      "ImageSrc":"www.frontfundr.com/Content/Upload/company_1223_20160601NewLogoforlaunch.png_20160601182554663.png",
      "Title":"Persephone",
      "TargetRaise":"$500,000",
      "EquityOffered":"12 %",
      "MinInvestment":"$250",
      "ClosingDay":"8/31/2016",
      "PercentRaised":"85%",
      "Description":"Farming, food, community and beer are what we do. World class, award-winning beer, Certified B Corp business practices and a commitment to having a positive impact drives our growth and passion."
   }
]
```
