# Join

A Ruby on Rails project that models private events, allowing users to create events, manage attendance, and interact with other users.
---

## Table of Contents

- [Introduction](#introduction)  
- [Features](#features)  
- [Models & Associations](#models--associations)  
- [Setup & Installation](#setup--installation)  
- [Usage](#usage)  
- [Extra Credit](#extra-credit)  
- [Contributing](#contributing)  

---

## Introduction

This project simulates a private Eventbrite-like application where:

- Users can create events.
- Users can attend multiple events.
- Events can be attended by many users.
- Events take place at a specific date and location.

The project emphasizes **ActiveRecord associations**, **foreign keys**, and **class name management** in Rails.

---

## Features

- User authentication with [Devise](https://github.com/heartcombo/devise).  
- Create, view, and manage events.  
- Attend events via a many-to-many relationship.  
- Display past and upcoming events separately.  
- Event details show attendees.  
- User profile pages list created and attended events.  

---

## Models & Associations

### User

```ruby
class User < ApplicationRecord
  has_many :created_events, class_name: "Event", foreign_key: "creator_id", dependent: :destroy
  has_many :attendances, dependent: :destroy
  has_many :attended_events, through: :attendances, source: :event
end

