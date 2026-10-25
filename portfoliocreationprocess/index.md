# Creating my e-Portfolio
## Step 1: Create your GitHub account and Install GitHub Desktop
Before building the site, you will need to create a GitHub account and also download GitHub Desktop.
- **Sign Up**: Register for a free account at [GitHub](https://github.com/) using your professional e-mail.
- **Install GitHub Desktop**: Download and install [GitHub Desktop](https://desktop.github.com/download/) on your local machine so you can push and/or pull code to and from your local/remote repository. 

## Step 2: Create your GitHub Pages Repository
GitHub Pages requires a specific repository naming convention to automatically host your site:
- Create a new public repositoryon GitHub.com by clicking on the **+** icon in the top right corner and select **New repository**. \
![Screenshot of where to create a new repository on github.com](/assets/img/CreateRepositoryWeb.png)

  - Name your repository **`<your_username>.github.io`** 
    - *If this is a public portfolio, select a username that is appropriate*
- Set the repository to **Public**, do not select a "README" at this time (since we will replace the one from the theme we will download) and select the appropriate license.
  - If you will be creating a new repository but not using a theme, please make sure that you are select the **ADD README** option as **ON**.
  - For my portfolio, MIT license was used.
- Click on **Create Repository**

## Step 3: Download the Jekyll Minimal Theme ZIP from GitHub
For my portfolio, I used the [Jekyll Minimal Theme](https://github.com/pages-themes/minimal). \
To acquire the same template and theme, you will need to download the theme assets locally.
- Go to the official theme repository on Github.com at https://github.com/pages-themes/minimal
- Click on the green **Code** button near the top right of the file list.
- Select **Download ZIP** from the dropdown menu to save the theme archive to your computer.
  - Since this is a ZIP file, you can download it to your *Downloads* folders for now, as we will extract the files to your repository. \

![Screenshot download minimal theme from github page](/assets/img/DownloadTheme.png)

## Step 4: Log In to GitHub Desktop and Mirror/Clone the Repository
Next, you want to me able to bring your newly created repository down to your local machine using GitHub Desktop.
- Open **GitHub Desktop** and log in with your GitHub credentials
- If this is your first time opening GitHub desktop:
  - The application will immediately prompt you to clone a repository. Select your newly create reposiotry from your account's list and choose your preferred destination folders and select **Clone**
- If this is not your first time logging into GitHub desktop, or you accidentally closed the pop-up when logging in for the first time on GitHub Desktop:
  - Go to **File > Clone Repository**
  - A pop-up will appear with your available repository or repositories.
  - Select the repository you'd like to mirror or clone on to your local machine
  - Choose the destination on your local machine of where you would like repository to be housed.
  - Select **Clone** \
  ![Screenshot for finding button for cloning repository on Desktop](/assets/img/CloneRepository1.png)

  ![Screenshot for selecting which repository to clone and identifying the destination](/assets/img/CloneRepository2.png)

- You should now see your repository cloned to your local machine as a folder.

## Step 5: Extract and Move the Theme Files
Next, we want to move the Jekyll minimal theme files into your cloned repository directory:
- [Unzip/extract](https://support.microsoft.com/en-us/windows/experience/storage-filemanagement/zip-and-unzip-files) the minimal theme archive you downloaded in Step 3.
- Select the cloned repository destination from Step 4 as your new destination for your unzipped files.

## Step 6: Push the Theme Files to GitHub.com
Now, we want to "push" or upload the theme files from your local directory to your repository on GitHub.com.
- Open **GitHub Desktop** and you should be able to see the newly added files under your repository on the left-hand pane.
- In order to "commit" the changes to your main branch, include a summary and a description of your changes.
- Push the "Commit to **main**" button
- Once completed, you should see that there are **"Push commits to the origin remote"** in the central part of the screen.
- Select **"Push Origin"**
  - *Note: The screenshots below are examples of different files. Please note that you may see more files being loaded than what I display as an example below.* \
  ![Screenshot for adding summary and description for committing changes](/assets/img/DescriptionPushOrigin.png)

  ![Screenshot for pushing origin](/assets/img/PushOrigin.png)


## Step 7: Configure the Minimal Theme (_config.yml)
To make sure that Jekyll recognizes the theme, you want to set up your central configuration file:
- Go back to your repository page on **GitHub.com**
- You should already see a _config.yml that was created from minimal theme extraction.
- Open the document and select the "Edit" option in the upper-right side.
- At a minimum, you will need to update the following fields:
  - title:
  - description:
- Make sure that you keep the "theme" as "theme: jekyll-theme-minimal".
- If you'd like to headshot, add your file to the assets > img folder under your local repository.
  - Once added, you will need to follow the same process as Step 6 and "push" your changes.
- Once completed, click the green **"Commit changes..."** button on the upper right side.
- For full visibility, I've provided the full code below for my own portfolio:
```
title: Elise Wallace
logo: /assets/img/EW_Headshot.jpg
description: My Portfolio
show_downloads: true
google_analytics:
theme: jekyll-theme-minimal
```

## Step 8: Draft Your Homepage Content
Next, we want to open the **index.md** file, which should be housed in the same folder as your **_config.yml** file.
- Open your index.md file and click the "edit" button.
- Use [markdown](https://www.markdownguide.org/) language to create your content.
- If you are adding any pictures, please make sure to add your photos to your assets > img folders and follow Step 6.
- For full visibility, my full markdown code is below:

````markdown
## About Elise Wallace

I am a data-driven Senior Account Manager and business analytics graduate student specializing in transforming complex operational and financial data into actionable strategy while empowering teams to build technical confidence.

### What Drives Me

For me, business analytics is only as powerful as the decisions and people it elevates. Throughout my career managing multi-million dollar account operations and streamlining enterprise workflows, I’ve found that true impact happens at the intersection of rigorous data analysis and team enablement.

I thrive on taking messy data sets, intricate forecasting models, and technical tools and distilling them into clear, actionable insights for cross-functional partners. Beyond hitting key performance metrics, my primary focus is fostering a collaborative environment where team members share knowledge, learn from complex problems, and continuously build their analytics capabilities. Whether I am architecting data solutions for high-stakes business processes or walking a teammate through a new analytical model, my goal is always to deliver clarity and leave people better equipped to drive success.

## Work Experience
\
![Amkor Logo](/assets/img/Amkor_logo_resized.jpg)
### Amkor Technology
**Senior Account Manager**\
*Mar 2026 - Present*
+ Lead end-to-end operational support for major technology accounts, serving as the core liaison between internal operations, supply chain, and client teams
+ Direct automation initiatives for revenue tracking, B2B invoicing, and inventory reporting to streamline operational workflows and improve data accuracy
+ Manage complex quarterly Request for Proposal (RFP/RFQ) submissions and analyze blended rate structures to ensure competitive positioning and billing precision
+ Direct cross-functional schedule adherence, material readiness, and cross-team execution for high-volume manufacturing

**Account Manager**\
*Mar 2024 - Feb 2026*
+ Managed daily account operations and supported client delivery timelines by aligning customer demand with manufacturing site capacity, substrate supply, and lead times
+ Conducted weekly short-term volume analyses and monthly long-term revenue forecasts to enhance executive decision-making and reporting precision
+ Recovered $1.2M+ in revenue leakage by conducting a thorough billing-versus-bookings validation audit
+ Partnered with cross-functional leadership to anticipate capacity bottlenecks, coordinate material readiness, and minimize operational escalations

**Senior Analyst, Account Management**\
*Jun 2020 - Feb 2024*
+ Reduced aging inventory from 20% to 2%, optimizing cash flow and minimizing operational holding risks
+ Managed New Product Introduction (NPI) material orders and accurately tracked Non-Recurring Engineering (NRE) costs, rebates, and billing schedules
+ Resolved complex pricing, invoicing, and order discrepancies by liaising between Finance, Operations, and Supply Chain teams

\
\
![Thermo Logo](/assets/img/thermo_logo_resized.png)
### Thermo Fisher Scientific
**Business Intelligence Intern**\
*May 2019 - May 2020*
+ Analyzed supply chain data of 30 manufacturing sites to create period-end scorecards and dashboards for providing site-level insights and target areas to divisional leaders with the goal of increasing customer allegiance scores, productivity, and realizing cost savings
+ Incorporating machine learning predictive analytics into existing dashboards and reports to proactively decrease operational costs and increase customer allegiance
+ Implementing best practices for data sources to reduce refresh loads and increase utility by creating dataflows and datasets to promote cloud-based computing

\
\
![Thermo Logo](/assets/img/mh_logo_resized.png)
### Millennium Health
**Team Lead, Client Services**\
*Jun 2014 - Aug 2018*
+ Improved processes and management of projects to streamline production and turnaround time for Specimen Resolution and its related departments via Lean/Six Sigma methods
+ Ran daily and monthly reports for sales and leadership teams via Business Intelligence tools, such as Excel, Power BI, or Tableau.
+ Provided leadership and support to staff including, but not limited to, deployment of new initiatives or processes, escalation handling, and talent development.

**Specimen Resolution Specialist**\
*Mar 2013 - May 2014*
+ Identifying and troubleshooting samples received with insufficient information or insufficient sample quantity, including handling of resolution documentation, re-processing samples, or rejecting samples.

## Professional Affiliations and Service
**OSBA Advisory Council, California State University San Marcos**\
*Aug 2022 - Present*

**Career Coach, California State University San Marcos**\
*Sep 2021 - Aug 2023*

## Education

**California State University San Marcos**\
Master of Science, Business Analytics\
*Aug 2026 - Aug 2027 (expected)*

**California State University San Marcos**\
Bachelor of Science, Business Administration – Global Supply Chain Management\
*Aug 2018 - May 2020*
+ GSCM Outstanding Student of the Year, 2020
+ James R. Meindl Student Leadership Award Recipient, 2020
+ President, Global Supply Chain Management Society

**Palomar College**\
Associate's Degree, Business Administration\
*Aug 2016 - May 2018*

**University of California, San Diego**\
Biochemistry\
*Sep 2008 - Mar 2010*

## Completed Projects
````

## Step 9: Verify Your Live Webpage
Once your changes have been committed, visit your life site at **`https://<your_github_username>.github.io/`** to view your completed portfolio.

## Step 10: Update README file
Now, we want to make sure that we are updating the README section. This should contain a brief description of what this repository is, any pertinent information that you would like your viewers to know, and any references that you may have used. 
- Go to **GitHub.com** and locate your README.md file in your repository.
- Use markdown language to update the contents.
- Commit changes.
