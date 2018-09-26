# mealpal-cli

**A set of command-line to make it possible to automate MealPal lunch booking.**

## Why ([![start with why](https://img.shields.io/badge/start%20with-why%3F-brightgreen.svg?style=flat)](http://www.ted.com/talks/simon_sinek_how_great_leaders_inspire_action))

The most popular places quickly sell out, so you have to book exactly at 5pm.

## Configuration

You need to specify your MealPal cookie **_mealpal_session** using `mealpal_session` environment variable:

- On Chrome, you can find it here: [chrome://settings/cookies/detail?site=secure.mealpal.com](chrome://settings/cookies/detail?site=secure.mealpal.com), or by pressing F12 and going to Application (tab) - Cookies (sidebar).

## Usage

```bash
./sleep-until -d "2018/09/26 17:10:00" && mealpal_session="YOUR_COOKIE_FROM_CHROME" ./list-available-lunches | ./filter-lunches -r "Restaurant name" | ./book-first-lunch
```
