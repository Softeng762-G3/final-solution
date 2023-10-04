Application：UiPath
Name: ScrapeData
Compatibility: Windows
Language: C#


Variable Types:
	String: year, make, model, importHis, fuelEconomy, price
	Int32: mileAge, price


Data that might not appear on the webpage:
	Import History
	Fuel Economy

Average data extraction time per page: Approximately 20 seconds

Browser Mode of Operation:
Fullscreen, Landscape orientation. Due to the usage of the 'pagedown' hotkey, do not scroll the screen during the automation process.

Notes:
There may be instances where the "Price" is not captured from some webpages.
As "trademe" updates their list of second-hand plug-in hybrid cars daily, you should first run ExtractListings.xaml (to fetch the latest URL list), and then run ScrapeData.xaml.
The number of URLs is around 1200. Hence, it's estimated that the total data extraction for these hybrid cars will take about 400 minutes.

Test Results:
After testing on dozens to hundreds of pages for data extraction, unexpected results have been addressed (most assign activities after extraction are set up to handle unexpected data). The extraction process meets the requirements set for the task.