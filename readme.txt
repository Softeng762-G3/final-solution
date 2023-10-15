<Environmentally Friendly Second-hand Cars>

[Github Repository]
https://github.com/Softeng762-G3/final-solution 

Although there are only four contributors in this repository, the contributions are shared by all group members. The breakdown of contributions are as follows:

Amy Rimmer: Presentation preparation, and tidy ups to ‘VisualiseResults’
Dinh Quyet: Implemented ‘VisualiseResults’ with Martin
Jo Bull: Implemented ‘ScrapeListingUrls’
Julie Kim: Completed final documentation, logging and code tidy ups
Kevin Wijaya: Implemented ‘MasterBot’ and deployment to Orchestrator
Martin Jurado Mesa: Implemented ‘VisualiseResults’ with Dinh
Qunzhi Zhou: Implemented ‘ScrapeListingInformation’

[Submission Files]
- readme.txt
- MasterBot: Implementation of a bot to run three sub-bots sequentially on orchestrator
- MasterProcess: Single bot with all process from three sub-bots merged 
- ScrapeListingUrls: Bot to scrape listing urls from Trade Me website
- ScrapeListingInformation: Bot to scrape vehicle information from listings
- VisualiseResults: Bot to visualise scrape data and save as file
- Final_Video_withOrchestrator.mp4: A recorded run of the solution through the orchestrator method.

[About the Project]
This is a project as a part of the course INFOSYS300/SOFTENG762 at the University of Auckland as of the Academic Year 2023. 

This repository contains a UiPath application that scrapes vehicle information from listings of second-hand Plug-in Hybrid Electric Vehicles (PHEV) on the Trade Me website. It then collates and displays this data in a document. The team aims to reduce the manual work required to search and navigate through numerous listings when purchasing a second-hand PHEV from Trade Me. This solution is designed to make the comparison process easier, potentially leading to increased purchases of environmentally friendly cars.

[Software Prerequisites]
This solution bot is compatible with Windows systems.The recommended browser mode of operation is fullscreen, landscape orientation.

To run the software successfully, ensure that the following software have been installed:
- UiPath Studio 2023.10.0
- UiPath Assistant 2023.10.0
- Microsoft Edge
- Microsoft Excel

[Running the project]
There are two methods to run the Trade Me scraping solution. One is through running a master process where the all three sub bot’s processes are merged into one bot to simply run the whole solution. The second method is to run the masterbot through the orchestrator and UiPath Assistant where the orchestrator will automate the three bots based on a scheduled trigger. The three bots ScrapeListingURL, ScrapeListingInformation and VisualiseResults can also be run individually manually by a user on UiPath.

The current UiPath bot version is modified to scrape a predefined number of web listings, optimising runtime due to Trade Me's large number of second-hand PHEV listings. The original bot scrapes all listings, but it takes about 20 seconds per listing, resulting in a 5-hour duration. As a result, the submitted bot provides a subset of website listings. However, you can easily adjust the number of listings to scrape or modify it within UiPath. You can do this on UiPath in the ScrapeListingInformation process sequence by changing the Range in the first Excel Application Scope, Read Range to A1:B_ (the number of listings you want to scrape).

* Option 1: Run MasterProcess (Recommended)
1. Open the MasterProcess folder in submission, and open Main.xaml in UiPath.
2. Click on "Manage Packages" in the top menu bar to check project dependencies and install them if needed.
3. To run the bot, click the "Debug File" button with the blue triangle icon, and the application will start.

* Option 2: Run in Orchestrator 
1. Open https://cloud.uipath.com/rpatisszjf/DefaultTenant/orchestrator_/
2. Sign in to the UiPath account by using the following authorised account through Continue with Google
	- Email: 762rpag3@gmail.com
	- Password: rpa762G3
3. Add the current machine to the tenant.
	a. Open the UiPath Assistant application on the machine. 
	b. Click the profile account icon on the top right. Select Preferences.
	c. Go to Orchestrator Settings, and select Connection Type to Client ID.
	d. Enter the following credentials:
		- Orchestrator URL: https://cloud.uipath.com/rpatisszjf/DefaultTenant/ 
		- Client ID: e3c4a766-1590-41a5-a024-6a2a0ceef100
		- Client Secret: sNfZ6miJWdJl0uGd
4. Set Up an unattended robot to your machine.
	a. In the UiPath Orchestrator cloud, go to Tenant at the top left.
	b. Select Robots, then select + Unattended setup. 
	c. Select Self hosted (Unattended Robot). Click next.
	d. Select Client as your machine. Click next.
	e. Click + Create a new robot account. 
	f. Type in the following.
		- Robot Name: Any name.
		- Domain\Username: Follow the instructions below:
		- Go to cmd and type “whoami”. Copy the Domain\Username from the cmd to the field. For example, yourname3333/name
	g. Select the name with your Domain\Username
	h. Select demo-rpa folder.
	i. Click Finish
5. On the Orchestrator, under My Folders, go to a folder named “demo-rpa”. 
6. Go to the Automation tab.
7. Under Processes, Press the  triangular start button of corresponding bot to run and select the following:
	a. Account that you set up from step 4)f)i)
	b. Machine: Select Client.
8. Press Start to execute the robot.

[Result]
The bots will generate a new PDF file named report.pdf at file location final-solution>VisualiseResults>report.pdf, which includes a visualisation of the information scraped from Trade Me PHEV listings. There are three graphs that show useful information for vehicle buyers, which are the proportion of car brands on the market, the average price of each car brand, and the average mileage for each car brand. This information can be additionally used along with the raw information saved as a spreadsheet in an Excel file named scrape_data.xlsx at file location final-solution>ScapeListing>scrape_data.xlsx for the users to easily compare and look for information that they need.

[Notes]
There are instances where some data are empty or unavailable in the scraped spreadsheet. The potential fields are price, import history, and fuel economy. This is not due to a bot mistake, but it is often the case that these fields are not provided by the particular sellers of PHEVs. The robot deals with this absence of information by filling in with empty or unavailable fields.

As "trademe" updates its list of second-hand plug-in hybrid cars daily, you should always run ScrapeListingsUrls.xaml to fetch the latest URL list first and then run ScrapeListingsInformation.xaml for information on all existing PHEV listings.
