

### Introduction

Welcome to Scorecard Builder.

This is an interface to develop credit risk scorecards. A credit risk scorecard is a tool to evaluate the level of risk associated with an application for credit. They are widely used in the banking and consumer finance industries across all products like mortgages, credit cards, auto finance and personal loans. You may have heard of the well-known FICO score used in the United States.

A scorecard comprises characteristics, attributes and score points. A characteristic is a variable which has been determined to be predicting the risk of an application. An attribute of a characteristic is a value or a group of values valid for that characteristic. A score point is the score assigned for that characteristic and attribute value. A very simple scorecard is shown in the diagram below. In this example, an applicant whose debt to income ratio is 50% will be assigned a score of 62 for this characteristic. The scores are added across all characteristics to arrive at the total score. Each score corresponds to a probability that the customer will go bad, i.e. default on their loan.

<img src="www/data-scorecard.png" title="Simple scorecard" alt="Simple scorecard" width="50%" />

This application allows you to develop a scorecard and covers all aspects of the credit scoring process. To learn more about this topic, refer to the book 'Credit Risk Scorecards' by Naeem Siddiqui (2005).

### Data

This tab allows you to upload data using which you will build a credit risk scorecard. In this version, it only accepts files stored in the CSV (comma-separated values) format.

It is not common to find such data online. The R package *smbinning* provides simulated data which can be used to learn how to build scorecards. Clicking on the link 'Download simulated data' will allow you to store this data as a CSV file in your computer. You can then upload this data onto this application.

Once you have uploaded the data, the interface will allow you to specify

* the type of the variable - numeric, integer, character or Date. The initial type will be auto-detected but can be modified by the user. The type of the variable is very important in the Binning tab - for example, you are not allowed to bin variables which are of type Date.

* the good/bad flag - a variable which identifies which accounts were good and which were bad in the uploaded data. The value 1 must be used for good accounts.

* the stratification variables - this is used in the Sample tab. When you are dividing the data into training and test samples, it is often a requirement that the distributions of few important variables are the same between the two samples. The good/bad flag is always chosen as a stratification variable by default. As the data will be grouped by these variables and then a random sample chosen for each group, too many groups may result in unexpected or erroneous behaviour. It is best to restrict the stratification to very few variables. One common situation which happens in practice that you want to maintain the same bad rate for every month, so if you have a variable which represents month you can choose that as a stratification variable.

* the binning variables - these are the variables which will be considered for initial binning. If there are variables which you are not going to bin at all, then uncheck that variable in the interface. Note that only variables which have been specified as of type numeric, integer or character can be binned.