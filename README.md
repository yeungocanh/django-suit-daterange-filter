# Date range filter for django-admin

[![Build Status](https://travis-ci.org/yeungocanh/django-suit-daterange-filter-python2.svg?branch=master)](https://travis-ci.org/yeungocanh/django-suit-daterange-filter-python2/)
[![codecov](https://codecov.io/gh/yeungocanh/django-suit-daterange-filter/branch/master/graph/badge.svg)](https://codecov.io/gh/yeungocanh/django-suit-daterange-filter)

Yet another filter for Django admin interface, adding possibility to lookup by date range. The filter is only compatible with [django-suit](https://github.com/darklow/django-suit) (does anyone use ugly stock admin now?) and python2.

![django-suit-daterange-filter](https://cloud.githubusercontent.com/assets/1592663/23668937/af6d1b54-0373-11e7-8ed2-3e4dcb9b3b54.png)

Key features:

* Support both DateField and DateTimeField
* Python2 compatibility
* User timezone support
* Simplest ever (< 128 SLOC)
* Well tested

## Installation

```sh
pip install django-suit-daterange-filter
```

Then add to the `settings.INSTALLED_APPS`:

```python
INSTALLED_APPS = (
    ...
    'date_range_filter',
)
```

## Usage

```python
# admin.py


from date_range_filter import DateRangeFilter

class EggAdmin(admin.ModelAdmin):
  list_filters = (
    'is_spam',
    'egg_count',
    ('timestamp', DateRangeFilter),
  )

```

## Issues

If you get JS errors about gettext, you should include django's built in i18n javascript, like this:

```python

class EggAdmin(admin.ModelAdmin):
  ...
  class Media:
    js = ['/admin/jsi18n/']
```

This module is heavily inspired by [django-daterange-filter](https://github.com/tzulberti/django-datefilterspec).
