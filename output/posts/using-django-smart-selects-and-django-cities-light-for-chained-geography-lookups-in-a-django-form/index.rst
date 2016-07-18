.. title: Using `django-smart-selects` and `django-cities-light` for chained geography lookups in a Django form
.. slug: using-django-smart-selects-and-django-cities-light-for-chained-geography-lookups-in-a-django-form
.. date: 2016-04-23 15:22:28 UTC-07:00
.. tags: django
.. category: Django
.. link:
.. description: How to
.. type: text

In re-writing my site [ForeignTeacherPay](http://foreignteacherpay.com/) in Django, I came across the problem of how to allow users to see schools listed by country, province, and city in China. FTP is a review site, so the ability to find and add schools by location is very important.

There is not a (published) list of all schools in China that hire foreign teachers, so users have to be able to add schools. In order to prevent duplicate schools listings,

In this post I will show you how to use `django-smart-selects` and `django-cities-light` together to prepopulate your database with geographic information (Country, Province/State, City), and then do chained selects in a Django model form.

1. Django and related packages

The two packages we will use in this tutorial are [`django-smart-selects`]() and [`django-cities-light`](). Install both using pip:

```bash
pip install -U django-smart-selects
pip install -U django-cities-light
```
