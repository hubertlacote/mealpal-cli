# mealpal-cli

**A set of command-line to make it possible to automate MealPal lunch booking.**

## Why ([![start with why](https://img.shields.io/badge/start%20with-why%3F-brightgreen.svg?style=flat)](http://www.ted.com/talks/simon_sinek_how_great_leaders_inspire_action))

The most popular places quickly sell out, so you have to book exactly at 5pm.

## Configuration

You need to specify your MealPal cookie **_mealpal_session** using `mealpal_session` environment variable:

- On Chrome, you can find it here: [chrome://settings/cookies/detail?site=secure.mealpal.com](chrome://settings/cookies/detail?site=secure.mealpal.com), or by pressing F12 and going to Application (tab) - Cookies (sidebar).

## Usage

A sample script is provided: [book-my-lunches](book-my-lunches):

```bash
# Edit the script with your mealpal session and the lunches that you want to book every 2 weeks, and execute
# it every two weeks on Sunday, by specifying the date of the first Monday of the schedule.
vi book-my-lunches

# Edit the script book-my-lunches and then execute:
./book-my-lunches -s "2019-01-21"

# Or specify another date, e.g. Monday in 2 weeks (Next Monday + 1 week):
./book-my-lunches -s "Monday + 1 week"
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
./tools/sleep-until -d "2018/09/26 17:10:00" && mealpal_session="YOUR_COOKIE_FROM_CHROME" ./tools/list-available-lunches | ./tools/filter-lunches -r "Restaurant name" -m "Meal name" | ./tools/book-first-lunch
```
