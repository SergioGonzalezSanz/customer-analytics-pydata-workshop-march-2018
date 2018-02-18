# Customer Analytics & PyData Workshop

Hi Everyone,

The goal of this workshop is to guide you on how to use PySpark to do customer analytics. Our target group are Spark & analytics beginners that want to get familiar with PySpark and data science. If you already are an avid Spark enthusiast and have data for breakfast everyday you might find this workshop too basic for you!

During this workshop, we will solve two tasks:

- **Task 1:** Characterise personas produced by a clustering algorithm. You can find the Zeppelin notebook containing the first task [here](https://github.com/SergioGonzalezSanz/customer-analytics-pydata-workshop-march-2018/blob/master/Task%201.json).
- **Task 2:** Build our own machine learning pipeline to predict an output. This exercise is described [here](https://github.com/SergioGonzalezSanz/customer-analytics-pydata-workshop-march-2018/blob/master/Task%202.json).

During the workshop (and after some mandatory pizza and drinks, nobody can code on an empty stomach), we will first describe each exercise and then we will let you solve them. In case you have any doubts or you get stuck, our colleagues will help you keep going and will give you some invaluable advice (don't hesitate to approach them!). After some time, we will discuss the results together and explore different solutions.

Since we have a limited time to finish the workshop, please make sure that you:

- Read the instructions carefully and follow all the steps before attending the meetup. We won't have time to install Python or Spark during the session so please make sure it is installed in your system (if it is not there yet) and it works correctly. We have added links and instructions on how to setup correctly for different OS below.
- Get familiar with the tasks we will solve. It will solve some precious time during the workshop.
- Open Zeppelin and make sure you can run PySpark (don't forget to choose the right interpreter using `%pyspark`).
- Download the workshop dataset and explore it before the session.
- Don't forget to bring your computer!!! (try to charge it before the session, we might not have enough plugs for everyone).
- And the most important of all: **enjoy!** We have put a lot of work on preparing this workshop so we hope you have a good time and learn a little bit more about PySpark and Customer Analytics.


## Getting started: get to know your data!

One of the most important tasks we must accomplish before doing any data analysis is getting to know the data we are working on. We have chosen a small open-source marking dataset from a Portuguese bank for this workshop. The customers in the dataset were approached on the phone regarding a new product offered by the bank (term deposit). You can download the file [here](https://archive.ics.uci.edu/ml/machine-learning-databases/00222/bank-additional.zip). There is a description of the dataset in this UCI repository [page](https://archive.ics.uci.edu/ml/datasets/Bank+Marketing).

The dataset contains information about the client demographics and whether they hired the new product or not.

1. Age (numeric)
2. Job family (categorical: 'admin', 'blue­collar', 'entrepreneur', 'housemaid', 'management', 'retired', 'self­ employed', 'services', 'student', 'technician', 'unemployed', 'unknown')
3. Marital status (categorical: 'divorced', 'married', 'single', 'unknown')
4. Education level (categorical: 'basic.4y', 'basic.6y', 'basic.9y', 'high.school', 'illiterate', 'professional.course', 'university.degree', 'unknown')
5. Has credit in areas? (categorical: 'no', 'yes', 'unknown')
6. Average yearly balance in euro (numeric)
7. Has a home loan? (binary: 'yes', 'no')
8. Has a personal loan (binary: 'yes', 'no')
9. Preferred communication channel (categorical: 'unknown', 'telephone', 'cellular')
10. Day of the month of the last contact (numeric)
11. Month of the last contact (categorical)
12. Duration of the last contact in seconds (numeric)
13. Number of times the customer has been contacted during the campaign, including this contact (numeric)
14. Number of days since the previous contact (-1 if not previously contacted)
15. Number of times the customer has been contacted during other campaigns (numeric)
16. Campaign outcome: has the customer hired the deposit? (categorical: 'no', 'yes')


## PySpark and Zeppelin Notebooks installation

This section describes how to install PySpark and Zeppelin notebooks for Windows, MacOS and Linux. If you are already using them you can skip this section.


### Windows

TO DO

### MacOS


#### Install python

Before installing Spark and Zeppelin, you must have Python installed on your computer. If you have `brew` already on your system, just type:

```
brew install python3
```

If you want, you can add the Python installation directory to your path:


You can find the full instructions [here](http://programwithus.com/learn-to-code/install-python3-mac/).

#### Install Spark

1. Go to your terminal
1. Make sure you have the brew caskets up to date
``
1.

Once the installation is finished, you should be able to run the PySpark shell:

```
pyspark-shell
```

Please check which version of Python the shell is using. Take a look to the first line that appears after typing `pyspark-shell`:

```
Python 3.6.4 (default, Jan  6 2018, 11:51:15)
[GCC 4.2.1 Compatible Apple LLVM 9.0.0 (clang-900.0.39.2)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
Using Spark's default log4j profile: org/apache/spark/log4j-defaults.properties
Setting default log level to "WARN".
To adjust logging level use sc.setLogLevel(newLevel). For SparkR, use setLogLevel(newLevel).
18/02/18 22:16:28 WARN NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
18/02/18 22:16:36 WARN ObjectStore: Failed to get database global_temp, returning NoSuchObjectException
Welcome to
      ____              __
     / __/__  ___ _____/ /__
    _\ \/ _ \/ _ `/ __/  '_/
   /__ / .__/\_,_/_/ /_/\_\   version 2.2.1
      /_/

Using Python version 3.6.4 (default, Jan  6 2018 11:51:15)
SparkSession available as 'spark'.
```

If you are not using Python 3, please change it exporting the right python to the `PYSPARK_PYTHON` environment variable:

```
export PYSPARK_PYTHON=python3
```

If you need a further explanation you can follow the instructions [here](https://medium.com/m/global-identity?redirectUrl=https://medium.freecodecamp.org/installing-scala-and-apache-spark-on-mac-os-837ae57d283f).


### Install Zeppelin notebooks

You can download the latest version of Zeppelin [here](https://zeppelin.apache.org/download.html). Once you have download and uncompress the file, go to the Zeppelin folder and type:

```
./bin/zeppelin-daemon.sh start
```

Once the daemon is running, you'll be able to access the notebook opening from your browser the address:

```
http://localhost:8080
```
It usually takes a few minutes to startup so don't rush it!

