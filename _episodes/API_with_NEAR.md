---
title: "Downloading data with with NEAR using API"
teaching: 5 min
exercises: 0
questions: "How to download data from website using API
objectives:

keypoints:
- "Postman, Python, API"
---

## Introduction
- Sometime, we need to use API to download the data from website when there are so many files and options to download.
- You can download data from Twitter, YouTube, Google etc using API. However you will need to register with the provider and get the API key or Bearer Token.
- This is an actual project where we will be downloading data from near website vista.um.co, with given username/password and API token.

## POSTMAN
- Postman is an API platform for building and using API
- In order to use Postman, you need to register an account and login with that:

![image](https://user-images.githubusercontent.com/43855029/168138485-100c60bb-ffe6-4270-91e0-88bcf5c6130d.png)

- If you are new to Postman, you will need to create Workspace to save your API query:

![image](https://user-images.githubusercontent.com/43855029/168138620-ea97ac73-a6ee-4130-81e0-bd6cd50b84c9.png)

- Once you have My Workspace, click on the + to open up the new workspace:

![image](https://user-images.githubusercontent.com/43855029/168138778-adf0a92d-e308-46a8-bd89-1f18780099f7.png)

- The following workspace opened:

![image](https://user-images.githubusercontent.com/43855029/168138850-0c2e8a6e-e50e-4fe6-b6fa-15326784cc6c.png)

- Here I will be downloading near data using shapefile (in zip format, created in other post)

- The approach that I am using is POST instead of GET.
- I also need to paste in the endpoint for the POST location and Authorization key in the Headers tab:

![image](https://user-images.githubusercontent.com/43855029/168139485-2c7984e4-5099-4086-aee1-1ed12a970c63.png)

- The most important task is the Body section, in the form data, there are 2 files that you need to insert:

- polygonFile with file type is File.
- jsonRequest with the string to download. Detail of json file is below:

```json
{"pipReportType":"PIN_REPORT",
"reportName":"F17_2021Q1",
"polygonInputOptions": { "polygonFormat": "ESRI_SHAPEFILE_ZIP",
"polygonNameAliasElement": "PageName" },
"startDateTime": "2021-01-01 00:00:00",
"endDateTime": "2021-03-31 23:59:59"
}
```

Note that: the reportName can be changed to match with the input shapefile.
The polygonNameAliasElement="PageName" is fixed with the shapefile variable names
The start and end DateTime can be altered

- Once everything is specified, hit Send then the job is submitted

![image](https://user-images.githubusercontent.com/43855029/168140571-8eb5be8a-88fb-43d1-ae92-ef80d0151186.png)

- Go back to Vista page and you will see the job submitted:
![image](https://user-images.githubusercontent.com/43855029/168140674-733120ad-5299-42d0-9558-6b7bef2cd2d5.png)

- 

