App Design/Overview README Template
===

# NutrionApp
---intro---

<img src="https://github.com/IOS-Codepath-Fall-2021/CO_OP/blob/master/K1i2PR2%20-%20Imgur.gif" width="400"/>
## Table of Contents
1. [Milestones](#Milestones)
2. [Overview](#Overview)
3. [Product Spec](#Product-Spec)
4. [Wireframes](#Wireframes)
5. [Schema](#Schema)

## Milestones
### Milestone 1
- [X] User can search for all common restaurant, foods and groceries item.
- [X] User can scroll and view all the food nutrition data similar to an Instagram display.
### Milestone 2
- [X] User can search for meals that match a certain nutrition plan.
- [X] User can pick the meals and see the grocery component break down the meal.
### Milestone 3
- [planned] User can set nutrition/health goals for themselves and the app will suggest tailored meal plans.
- [planned] Settings.

## Overview
### Description
Nutrionapp is a nutrition app that assists people in pursuing a healthy and nutrient balanced lifestyle. The app is powered by the Nutritionix Database that has data on over 1 million data points on common foods, grocery and restaurant items. The app can suggest, track, customize a healthy diet for you ensuring each one of your users to be as healthy as possible. The app can also suggest the most cost efficient location to purchase these items.  
### App Evaluation
[Evaluation of your app across the following attributes]
- **Category:** Lifestyle/ Diet/ Health
- **Mobile:** This app would be primarily developed for mobile but would perhaps be just as viable on a computer, such as tinder or other similar apps. Functionality wouldn’t be limited to mobile devices, however mobile versions could potentially have more features.
- **Story:** Gather general health status and analyze users' food choices, to suggest a diet plan that helps users to balance nutrients, and reach their goals. This app will coach and support the user in this diet process.
- **Market:** Any individual of any age group could choose to use this app as this app does not have access accounts nor store any user information; This makes our app very secure and accessible. This app will also consider all users' culture foods as well truly being inclusive to all populations.
- **Habit:** This app could be used as often or often as the user wanted depending on their own will and perseverance on a healthy life. It's also what exactly the user is  looking to improve in their diet and health.
- **Scope:** First we would start with just suggesting basic diet plans to users, then perhaps this could evolve into an individual diet/health coach that is tailor made for all users, as this progresses we broaden the apps usage and funcatilties. Eventually the application will have a large potential for use and be supported with apple health or samsung health.

## Product Spec

### 1. User Stories (Required and Optional)

**Required Must-have Stories**

* User can search for meals that match a certain nutrition plan
* User can pick the meals and see the grocery component break down the meal
* User can scroll and view all the food nutrition data similar to an instagram display 
* User can set nutrition/health goals for themselves and the app will suggest tailored meal plans
* User can search for all common restaurant, foods and groceries item
* Settings 

**Optional Nice-to-have Stories**

* Profile for users login/ logout
* Profile can track user nutrition progress and balance
* User can find the most cost efficient store or location to buy the suggested grocessaries
* User can know the price of the nuttuionasit restaurants
* User can enter personal health status (weight, blood pressure, etc...) to have a better customization of their nutrition coaching process

### 2. Screen Archetypes

* [Home screen - Users will be able to view the nutrition categories]
   * [Upon opening the app a general election will appear for quick selection of food categories listed]
* [Search screen- Users can do explicit searches of food products]
   * [User can search for meals that match a certain nutrition plan] 
   * [User can search for all common restaurant, foods and groceries item]
   * [User can set nutrition/health goals the app will suggest meal plans]
* [Food item screen- (like instagram) where user can scroll infinitely to browse groceries/ commo food/ meals/ etc]
   * [User can pick the meals and see the grocery component break down of the meal]
   * [User can scroll and view all the food nutrition data similar to an instagram display]
* [Settings screen- each app instance can be customized and saved]
   * [Settings]

### 3. Navigation

**Tab Navigation** (Tab to Screen)

* [Settings]
* [Search]
* [Restaurants]

Optional:

* [Maps]
* [Settings] --> [Profile]
* [Restaurants] --> [Quick Selection]

**Flow Navigation** (Screen to Screen)

* [Home screen ->]
   * [Settings]
   * [Food item screen]
   * [Search]
* [Settings ->]
   * [Home Screen]
* [Food item screen ->]
   * [Home]
   * [Setting]
   * [Search]
* [Search ->]
   * [Home]
   * [Setting]
   * [Food item screen]


## Wireframes
[Picture of hand sketched wireframes section:]

<img src="https://github.com/IOS-Codepath-Fall-2021/CO_OP/blob/master/11-1-21%2C%2011_13%20PM%20Microsoft%20Lens.jpeg" width=600>

### [BONUS] Digital Wireframes & Mockups

### [BONUS] Interactive Prototype

## Schema 
[This section will be completed in Unit 9]
### Models
[A table of models for Reading from database] {optional- currently app do not need user database- that is Beta version}
   | Property      | Type     | Description |
   | ------------- | -------- | ------------|
   | objectId      | String   | unique id for the user post (default field) |
   | author        | Pointer to User| image author |
   | image         | File     | image that user posts |
   | caption       | String   | image caption by author |
   | commentsCount | Number   | number of comments that has been posted to an image |
   | likesCount    | Number   | number of likes for the post |
   | createdAt     | DateTime | date when post is created (default field) |
   | updatedAt     | DateTime | date when post is last updated (default field) |
   
### Networking
[Add list of network requests by screen ]
   - Home Table View Screen
      - (Read/GET) Query to retrieve from database - defualt
      - (Fetch/GET) Create a post request to ask for food suggestions
      - (Fetch/GET) Fetch news and daily reminders form the API
      - (Fetch/POST) Send to API filter request 
   - Search Screen
      - (GET/POST) Query to retrieve from database
        -- for grocery
        -- for resturants
        -- for common foods
   - Profile Screen (Beta)
      - (Read/GET) Query logged in user object
      - (Update/PUT) Update user profile contents
[Create basic snippets for each Parse network request]
      - (Read/GET) Query all posts where user is author -> the code below will be the Query calls for all our objects and endpoints.
         ```swift
            let params = ["username":"john", "password":"123456"] as Dictionary<String, String>

            var request = URLRequest(url: URL(string: "http://localhost:8080/api/1/login")!)
            request.httpMethod = "POST"
            request.httpBody = try? JSONSerialization.data(withJSONObject: params, options: [])
            request.addValue("application/json", forHTTPHeaderField: "Content-Type")

            let session = URLSession.shared
            let task = session.dataTask(with: request, completionHandler: { data, response, error -> Void in
                print(response!)
                do {
                    let json = try JSONSerialization.jsonObject(with: data!) as! Dictionary<String, AnyObject>
                    print(json)
                } catch {
                    print("error")
                }
            })

            task.resume()
         ```
[OPTIONAL: List endpoints if using existing API such as Yelp]
   | Property           | Type           | Description c                                                                  | Endpoints |
   | -------------------|----------------|--------------------------------------------------------------------------------|---------  |
   | search_food        | Dictionary-JSON| GET/POST-basic search for food options                                         | https://trackapi.nutritionix.com/v2/search/instant |
   | search_restaurants | Dictionary-JSON| GET/POST-basic search for resturant suggestions                                | https://trackapi.nutritionix.com/v2/locations |
   | search_nutrients   | Dictionary-JSON| GET/POST-basic search for nutrient dataBase contents                           | https://trackapi.nutritionix.com/v2/natural/nutrients |
   | natural/nutrients  | String-QUERY   | users can get detailed nutrient break down when they search for a product      | https://trackapi.nutritionix.com/v2/natural/nutrients |
   | commentsCount      | String-QUERY   | users can look up the nutrition information for any branded food item api(GET) | https://trackapi.nutritionix.com/v2/search/item|
   | Calculator         | String-QUERY   | nutrient calculator that can measure the dietary status of user|               | |


SetUp help:https://stackoverflow.com/questions/24321165/make-rest-api-call-in-swift/46895243#46895243 , https://matteomanferdini.com/network-requests-rest-apis-ios-swift/ , https://medium.com/@nutanbhogendrasharma/consume-rest-api-in-swiftui-ios-mobile-app-b3c5d6ecf401
