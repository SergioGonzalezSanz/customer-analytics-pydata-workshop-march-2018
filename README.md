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

One of the most important tasks we must accomplish before doing any data analysis is getting to know the data we are working on. We have chosen a small open-source marking dataset from a Portuguese bank for this workshop. The customers in the dataset were approached on the phone regarding a new product offered by the bank (term deposit). There is a description of the dataset in this UCI repository [page](https://archive.ics.uci.edu/ml/datasets/Bank+Marketing). We have added a cell in the tasks to download the data in parquet format from the server we've put together for this workshop so there is no need for you to download the data from the UCI repository.

The dataset contains information about the client demographics and whether they hired the new product or not.

1. **age:** age (numeric).
2. **job:** job family (categorical: 'admin', 'blue­collar', 'entrepreneur', 'housemaid', 'management', 'retired', 'self­ employed', 'services', 'student', 'technician', 'unemployed', 'unknown').
3. **marital:** marital status (categorical: 'divorced', 'married', 'single', 'unknown').
4. **education:** education level (categorical: 'basic.4y', 'basic.6y', 'basic.9y', 'high.school', 'illiterate', 'professional.course', 'university.degree', 'unknown').
5. **default:** has credit in areas? (categorical: 'no', 'yes', 'unknown').
6. **housing:** has a home loan? (binary: 'yes', 'no').
7. **loan:** has a personal loan (binary: 'yes', 'no').
8. **contact:** preferred communication channel (categorical: 'unknown', 'telephone', 'cellular').
9. **month:** last contact's month (categorical).
10. **day_of_week:** last contact's week day (categorical).
11. **duration:** duration of the last contact in seconds (numeric). This attribute shouldn't be used for classification since it's unknown before contacting the customers and directly correlated with the result of the call.
12. **campaign:** number of times the customer has been contacted during the campaign, including this contact (numeric).
13. **pdays:** number of days since the previous contact (-1 if not previously contacted).
14. **previous:** number of times the customer has been contacted during previous campaigns (numeric).
15. **poutcome:** previous marketing campaign result (categorical: 'failure', 'nonexistent', 'success').
16. **emp.var.rate:** employment variation rate - quarterly indicator (numeric).
17. **cons.price.idx:** consumer price index - monthly indicator (numeric).
18. **cons.conf.idx:** consumer confidence index - monthly indicator (numeric).
19. **euribor3m:** 3-month rate EURIBOR (numeric).
20. **nr.employed:** number of employees - quarterly indicator (numeric).
21. **y:** campaign outcome: has the customer hired the deposit? (categorical: 'no', 'yes').

## PySpark and Zeppelin Notebooks installation

This section describes how to install PySpark and Zeppelin notebooks for Windows, MacOS and Linux. If you are already using them you can skip this section.

### MacOS

#### Requirements
Please make sure you have [Homebrew](https://brew.sh/) installed on your
machine. You will also need to have XCode installed (you can download it from the App
Store), along with the command line tools that you can install with:

```bash
xcode-select --install
```

#### Install python

Before installing Spark and Zeppelin, you must have Python installed on your computer. Python 3.6 might cause some problems depending on the PySpark version you have on your machine, so we will use Python 3.5 on this workshop.

If you have `brew` already on your system, just type:

```
brew install pyenv
pyenv install 3.5.5
```

It will install Python in `$HOME/.pyenv/versions/3.5.5`. Now, you must set the Python version you want to use with PySpark:

```
export PYSPARK_PYTHON=$HOME/.pyenv/versions/3.5.5/bin/python3.5
```

##### Python dependencies

`Task 2.json` uses the `requests` library to upload the model scores to our ranking server. Please install it using `pip`:

```
pip3 install --upgrade requests
```

#### Install Spark

1. Go to your terminal
1. Make sure you have the brew caskets up to date, then install `apache-spark`:
   ```
   brew update
   brew upgrade
   brew install apache-spark
   ```
1. Reload your terminal

Once the installation is finished, you should be able to run the PySpark shell:

```
pyspark
```

Please check which version of Python the shell is using. Take a look to the
first line that appears after typing `pyspark`:

```
Python 3.5.5 (...)
[GCC 4.2.1 Compatible Apple LLVM 9.0.0 (clang-900.0.39.2)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
2018-03-04 19:24:04 WARN  NativeCodeLoader:62 - Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
Setting default log level to "WARN".
To adjust logging level use sc.setLogLevel(newLevel). For SparkR, use setLogLevel(newLevel).
2018-03-04 19:24:07 WARN  Utils:66 - Service 'SparkUI' could not bind on port 4040. Attempting port 4041.
2018-03-04 19:24:07 WARN  Utils:66 - Service 'SparkUI' could not bind on port 4041. Attempting port 4042.
2018-03-04 19:24:07 WARN  Utils:66 - Service 'SparkUI' could not bind on port 4042. Attempting port 4043.
Welcome to
      ____              __
     / __/__  ___ _____/ /__
    _\ \/ _ \/ _ `/ __/  '_/
   /__ / .__/\_,_/_/ /_/\_\   version 2.3.0
      /_/

Using Python version 3.5.5 (default, Mar  4 2018 19:16:41)
SparkSession available as 'spark'.
>>>
```

If you need a further explanation you can follow the instructions [here](https://medium.com/m/global-identity?redirectUrl=https://medium.freecodecamp.org/installing-scala-and-apache-spark-on-mac-os-837ae57d283f).


### Install Zeppelin notebooks
Zeppelin can be found on `brew`. Install it by typing:

```bash
brew install apache-zeppelin
```

Alternatively, you can download the latest version of Zeppelin
[here](https://zeppelin.apache.org/download.html).

When Zeppelin is installed with `brew`, you can launch it from anywhere with the
command:

```bash
zeppelin-daemon.sh start
```

To interrupt Zeppelin, type:

```bash
zeppelin-daemon.sh stop
```

If you downloaded the Zeppelin archive, uncompress it and jump into its
folder. Then type:

```
./bin/zeppelin-daemon.sh start
```

Once the daemon is running, you'll be able to access the notebook opening from
your browser the address `http://localhost:8080`. It usually takes a few minutes
to startup, so don't rush it!

### Ubuntu

#### Requirements
You need to have Java 7 or 8, and Scala installed. You can check your Java
version with:

```bash
$ java -version
```

In case the Java version does not match with the requirements, you can install
version 8 with the following:

```bash
$ sudo apt-add-repository ppa:webupd8team/java
$ sudo apt-get update
$ sudo apt-get install oracle-java7-installer
```

Scala is another requirement for PySpark. You can download the latest version of
Scala from the [official Scala
archive](http://www.scala-lang.org/files/archive/). Alternatively, you can run
the following commans:

```bash
$ wget http://www.scala-lang.org/files/archive/scala-2.12.5.deb
$ sudo dpkg -i scala-2.12.5.deb
$ rm scala-2.12.5.deb
```

To check that the installation was successful, just run:

```bash
$ scala -version
```

#### Python environment
A virtual environment is recommended in order to install all the Python
dependencies. You can use the environment manager of your choice, but make sure
to use Python version 3.5 as the latest 3.6 will probably not work.

Once the virtual environment is ready, install all the packages with `pip`:

```bash
(venv) $ pip install py4j
(venv) $ pip install pyspark
```

When it's done, check the installation:

```
(venv) $ pyspark
Python 3.5.2 (default, Nov 23 2017, 16:37:01)
[GCC 5.4.0 20160609] on linux
Type "help", "copyright", "credits" or "license" for more information.
2018-03-24 10:43:03 WARN  Utils:66 - Your hostname, brainBox resolves to a loopback address: 127.0.1.1; using 192.168.0.158 instead (on interface wlp58s0)
2018-03-24 10:43:03 WARN  Utils:66 - Set SPARK_LOCAL_IP if you need to bind to another address
2018-03-24 10:43:03 WARN  NativeCodeLoader:62 - Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
Setting default log level to "WARN".
To adjust logging level use sc.setLogLevel(newLevel). For SparkR, use setLogLevel(newLevel).
2018-03-24 10:43:04 WARN  Utils:66 - Service 'SparkUI' could not bind on port 4040. Attempting port 4041.
Welcome to
      ____              __
     / __/__  ___ _____/ /__
    _\ \/ _ \/ _ `/ __/  '_/
   /__ / .__/\_,_/_/ /_/\_\   version 2.3.0
      /_/

Using Python version 3.5.2 (default, Nov 23 2017 16:37:01)
SparkSession available as 'spark'.
>>>
```

##### Python dependencies

`Task 2.json` uses the `requests` library to upload the model scores to our ranking server. Please install it using `pip`:

```
pip3 install --upgrade requests
```

#### Zeppelin Notebook
You can download the Zeppelin Notebook fom the [Apache Zeppelin download
page](https://zeppelin.apache.org/download.html) (the binary package with the
Spark interpreter will do). From command line, just download the Zeppelin
archive and extract it:

```bash
$ wget http://ftp.heanet.ie/mirrors/www.apache.org/dist/zeppelin/zeppelin-0.7.3/zeppelin-0.7.3-bin-netinst.tgz
$ tar xvf zeppelin-0.7.3-bin-netinst.tgz
```

Once the archive is available, run the Zeppelin Notebook like this (remember to
**run Zeppelin when the virtual environment is activted!**):

```bash
(venv) $ cd zeppelin-0.7.3-bin-netinst/bin
(venv) $ ./zeppelin-daemon.sh start
```

It will take a while for Zeppelin to actually start. You can check whether it's
online by opening a browser at `http://localhost:8080`, or you can use the same
script to query for the status:

```bash
(venv) $ ./zeppelin-daemon.sh status
```

When you're done with the notebook, just run:

```bash
(venv) $ ./zeppelin-daemon.sh stop
```
