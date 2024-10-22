# Beats-Pi
Elastic Beats.  You know, for Pi.

### Updates 28 March 2020
Added support for arm64 architecture in case you're running a 64-bit OS on your Pi.

### Updates 17 March 2020
v7.6.1 of all the Beats are now live!  I changed the GPG key, so you'll need to re-download using the instructions below.
ENJOY!

## About this repo
Elastic Beats are lightweight data shippers that collect and send information back to Logstash, your Elasticsearch cluster, or another output of your choosing.  However, Elastic doesn't package them for Raspberry Pi, so even if you connect to Elastic's apt repo, you won't be able to install Beats.

You can build the beats from source if you want, and I go over how to do that in my easyBEATS fork.  However, here I make it easy.  I've packaged the Beats and put them in an apt repo that you can use on your Raspberry Pi.  

## Connect to the repo

First you'll need to install the gpg key for this repo.  This helps to ensure that the package hasn't changed between the repo and your Pi.

```
wget -O - https://raw.githubusercontent.com/RaoulDuke-Esq/Beats-Pi/master/beats-pi.gpg.key | sudo apt-key add -
```

Next, add the repo to your apt sources.

```
echo "deb https://raw.githubusercontent.com/RaoulDuke-Esq/Beats-Pi/master buster main" | sudo tee -a /etc/apt/sources.list.d/beats-pi.list
```

That's it!  Pretty easy, right?

## Installing Beats

Now you can update apt with the new packages found in this repo.

```
sudo apt-get update
```

Install whichever Beat you'd like.

```
sudo apt-get install metricbeat
```

## Configuring Beats

If you're not already familiar with how to configure Beats, check out [Elastic's documentation](https://www.elastic.co/guide/index.html).

## Upgrading Beats
If you've previously installed Beats using this repo, don't worry!  When you upgrade you will be prompted on whether to keep or replace your existing beat.yml file.  Just type N to keep your existing version.
