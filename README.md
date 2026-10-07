# OpenFoods

👋 Hi! Welcome to your app coding excercise.

This is a very simple application. Your recruiter should provide you with a unique URL for the API, this is just for you. You are asked to write the app that will display a list of foods from the API. The API also allows you to like and unlike foods.

## Minimum requirements

- Fork or clone the repo.
- Parse the list of foods.
- Display the foods in the order the service defines them from the 0th page. The app should display:
  - The name of the food.
  - The description of the food, this is variable length so the cells must be properly sized to the content or this can be truncated and the full description can be shown on another screen the user navigates to.
  - The country of origin, this could be the text, an emoji, an image or something else.
  - Do you like this food? This should be an image or a symbol of some kind.
- Handle any server side errors or slow requests gracefully.
- When done, send a zipped version of the project via email.
  - Please delete the template folders you didn't use and zip the top-level OpenFoods-2025 folder.

We've provided a template Android project for Android candidates and template SwiftUI and UIKit projects for iOS candidates.  Please submit only one solution.  Please feel free to use these or create a brand new project utilising whatever technologies you think are most appropiate for the role that you are applying for.  Please disclose any AI use in your tech test. 

## Bonuses (in no particular order)

- Access all the pages of the results.
- Add a button to like or unlike a food and then reload the list of foods.
- Show the image of the food.
- Show when the food was last updated.
- Animate or highlight a food when it is selected (e.g. make it "bigger", in an animated fashion.)
- Add tests.
- Cache images.
- Anything else you might think of that showcases a user interface feature, for example a parallax effect, the list is endless.

## What the assignment will be judged on

- Accuracy of the result (e.g. is the cell sizing pixel perfect, dates are properly formatted, the app doesn't crash, project builds and runs with no extra step, etc.)
- Proper usage of Android or Apple APIs (e.g. are cells properly reused, a back button must have a proper title, how well does it scale to various device sizes, etc.)
- Overall code quality: clarity, conciseness, quality of comments. Robustness and maintainability matter a lot more than clever one liners.
- If you end up short on time and/or can't fix a specific bug or finish a given feature, update this readme with what the bug is, and how you think you can fix had you more time.
- Bonuses are exactly that, bonuses. If you can complete one or more, good. Otherwise, don't sweat it.
- If you can't complete something, explain why, how you reached that conclusion and potential options to complete it.

## What the assignment will not be judged on

- UI performance (e.g. framerate), as long as it's reasonable. Feel free to indicate in the code if / why something would affect the framerate, and a potential solution to it.
- If you try to complete a bonus and can't finish it, that's fine. We recommend using git commits / tags to indicate where the bonuses start in the history, so we can easily reset the branch at that commit and validate the minimum requirement.

## API

Your recruiter should share with you a unique URL for the API. `userId` below is unique to you. You will find that in the unique URL provided, the API will not work without this. If you have any issues please reach out over email.

### Food

You can `GET` a list of foods from `api/v1/<userId>/food/<page>`. For example the 1st page could be accessed with `api/v1/jdoe/food/0`.

This API will give you a list of foods. Sometimes this service can take _awhile_ to respond. A food has at the minimum:

- `id` - You can use this to like and unlike foods.
- `name` - Name of the food.
- `isLiked` - Do you like this?
- `photoURL` - An absolute URL to an image of food that _probably_ exists.
- `description` - A description of the food. This could be empty or a very long string.
- `countryOfOrigin` - An ISO-3166-1 Alpha-2 code of a country that is _almost always_ real that could be nicely presented.
- `lastUpdatedDate` - When the food was added to the system or when you last liked or unliked it in the standard ISO-8601 format.

```json
{
  "foods":
  [
    {
    "id": 99,
    "name": "French Onion Soup",
    "isLiked": false,
    "photoURL": "https://example.com/images/soup.jpg",
    "description": "French onion soup is a soup usually based on meat stock and onions, and often served gratinéed with croutons or a larger piece of bread covered with cheese floating on top. Ancient in origin, the dish underwent a resurgence of popularity in the 1960s in the United States due to a greater interest in French cuisine. French onion soup may be served as a meal in itself or as an entrée.",
    "countryOfOrigin": "FR",
    "lastUpdatedDate": "1970-01-01T00:00:00Z"
    }
  ],
  "totalCount": 1
}
```

Up to 10 foods will be returned per page.  The total number of foods will always be returned so you can determine if you should access the next page. We _could_ add extra foods when we assess your tech test.

### Like

You can `PUT` a like to `api/v1/<userId>/food/<id>/like` to set `isLiked` to `true` and update `lastUpdatedDate` to now. This service _usually_ works but can throw errors sometimes. If the food has been succesffuly updated the value of `success` will be `true`.

```json
{ "success": true }
```

### Unlike

You can `PUT` an unlike to `api/v1/<userId>/food/<id>/unlike` to set `isLiked` to `false` and update `lastUpdatedDate` to now. This service _usually_ works but can throw errors sometimes. If the food has been succesffuly updated the value of `success` will be `true`.

```json
{ "success": true }
```

## Gen AI

We recognize AI tools  can be useful in professional workflows, and we want to take a clear and fair approach to their use in our interview process. Our goal is to understand your thinking, decision-making, and experience — not just the final output. With that in mind, we ask that all candidates follow these guidelines:
- Disclose any AI use during the interview process — whether for generating code, writing, visuals, or research.
- Take ownership of your work. If AI assists you, be prepared to explain your approach and why your solution is effective.
- Use AI as a support, not a crutch. We welcome AI-assisted work when it enhances your thinking — but unedited or uncritical copy-paste responses are discouraged and may reflect poorly on your candidacy.

## Fin

Happy coding!
