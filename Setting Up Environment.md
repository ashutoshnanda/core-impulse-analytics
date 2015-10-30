#What are our tools?

We'll be using R, RStudio, and Google Analytics in order to analyze the web data generated on the CORE Impulse page.

#R (you ready?)

(Yes, the obligatory R pun was totally necessary; I'll try hard [and probably fail] to refrain from making more puns later on.)

##What is R?

R is a statistical programming language that has many built-in statistical routines that we may need to run. Plus, it's open source and people are contributing cool packages every day!

##Installing R

You can go ahead and install R from [here](https://cran.rstudio.com/). (CRAN stands for Comprehensive R Archive Network, which means a set of computers that store R code and documentation; the RStudio one will automatically link you to the server closest to you.) Just follow the instructions, and it should be fine.

#RStudio

##What is RStudio?

RStudio is an Integrated Development Environment (IDE) for R; a good analogy is Eclipse is for Java what RStudio is for R. It has great features to help your workflow within R, and to paraphrase the words of one of my favorite data scientists: "If you're using RStudio, great; if you're not, what are you doing with your life?"

##Installing RStudio

You can install RStudio by following the instructions [here](https://www.rstudio.com/products/rstudio/download/). Again, following the instructions should ensure you don't have any problems.

##Testing RStudio

Open up the RStudio application. You should eventually see a 4 pane layout. Try typing `3 + 5` in the console portion (bottom left if you left all options as default), and you should see it print out:
```
[1] 8
```
Hopefully it works!

#Google Analytics

Google does this really nice thing where they will tell you who has been browsing on your website, but with a catch: you must let them index your page. This as a service is called Google Analytics, and since Google will come along and index your page at some point using Google power, we may as well take the benefit they're giving us. :)

By connecting R and Google Analytics, we will be able to use the power of R on the web analytics data. We'll be using the `RGA` package. Let's install it by typing `install.packages('RGA')` on the console. After it has successfully installed, type `authorize()`. This should open up your favorite web browser and prompt you to connect RGA with your Google account; make sure you pick the account on which you got Google Analytics access! Once this process is done, head back to RStudio. Then, type `getwd()`. You should see some path printed out; make sure to note this down since it's important for later. RGA basically just created a token for itself (in a file called `.ga-token.rds` within the directory that just got printed) to access the analytics data that you could manually browse through, but now, you have the power of R working on that data instead of you just looking at it.

Let's create a folder where all your code will live for CORE Impulse web analytics; it'll be referred to as `(DIR)`. Move the token from the path printed above into `(DIR)`. You can check this worked by typing `dir(all.files = T)` into the console and making sure the token file shows up in the output. Now, let's play with some data!

To make sure we're getting the data for CORE Impulse, we need to specify the profile ID in the functions that actually get data from Google Analytics. We can check the ID by typing `my.profile.id <- list_profiles()$id`; this will store the specific ID in a variable named `my.profile.id`. Now, let's run the following code chunk:
```
ga_data <- get_ga(profile.id = my.profile.id, start.date = "30daysAgo", end.date = "yesterday",
                  metrics = "ga:users,ga:sessions,ga:pageviews")
```
Then type `ga_data` into the console to see the data we obtained; woo, we just did our first bit of web analytics through R!