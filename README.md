# mealpal-cli

**A set of command-line to make it possible to automate MealPal lunch booking.**

## Why ([![start with why](https://img.shields.io/badge/start%20with-why%3F-brightgreen.svg?style=flat)](http://www.ted.com/talks/simon_sinek_how_great_leaders_inspire_action))

The most popular places quickly sell out, so you have to book exactly at 5pm.

## Configuration

You need to find your MealPal cookie **_mealpal_session**:

- On Chrome, you can find it here: [chrome://settings/cookies/detail?site=secure.mealpal.com](chrome://settings/cookies/detail?site=secure.mealpal.com), or by pressing F12 and going to Application (tab) - Cookies (sidebar).

## Requirements

- Instructions for Ubuntu:

```bash
# Install jq (Command-line JSON processor)
sudo apt install jq
```

- Instructions for Mac OSX:

Using Homebrew (For details about installing homebrew, see http://brew.sh):

```bash
brew install jq
```

## Usage

Book easily a single lunch with [book-lunch](book-lunch):

```bash
./book-lunch -c "YOUR_COOKIE_FROM_CHROME" -d "tomorrow" -r "Restaurant name" -m "Meal name"
```

Schedule all your lunches for the next two weeks - a sample script is provided: [book-my-lunches](book-my-lunches):

```bash
# Edit the script to specify the lunches that you want to book every 2 weeks
vi book-my-lunches

# Specify the first Monday of the schedule
./book-my-lunches -s "2019-01-21"
```

Or feel free to use directly the command line tools:

```bash
# Print usage
./tools/list-all-lunches -h
./tools/list-available-lunches -h
./tools/filter-lunches -h
./tools/book-first-lunch -h
./tools/sleep-until -h

# One liner to book a lunch
./tools/sleep-until -d "2018/09/26 17:10:00" && MEALPAL_SESSION="YOUR_COOKIE_FROM_CHROME" ./tools/list-available-lunches | ./tools/filter-lunches -r "Restaurant name" -m "Meal name" | ./tools/book-first-lunch
```
