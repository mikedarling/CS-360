# Mobile2App Inventory Manager

## Briefly summarize the requirements and goals of the app you developed. What user needs was this app designed to address?

The application is intended to allow its users to manage a catalog of products and inventory levels of those products. 

## What screens and features were necessary to support user needs and produce a user-centered UI for the app? How did your UI designs keep users in mind? Why were your designs successful?

The Application features the following screens:

- a login and registration screen,
- a main screen which displays the grid of products,
- an upsert screen that allows users to add or update products, and
- a settings screen that allows users to enable or disable SMS notifications.

The UI design tried to assist users by leveraging well-known conventions and design cues, such as the plus icon in the floating action button being used to indicate that it would display the capability to add a product to the catalog and the gear in the app bar identifying a link to the application settings.

## How did you approach the process of coding your app? What techniques or strategies did you use? How could those be applied in the future?

Most of my approach consisted of working from the presentation down. That is, first I would create the layout, which I would then tie to a "controller". The "controller" would mainly deal with interactions with the UI. All of the business logic is contained in a service layer that communicates to the DAL. I typically will "use" a method in code before I've even declared it a class, then I'll use the IDE's intell-sense functionality to stub that method, at which point I'll also go write that method. I find this approach really helps create methods that do a good job of representing a unit of work.

## How did you test to ensure your code was functional? Why is this process important and what did it reveal?

Testing was all done with built-in emulator. If at any point something did not behave how I expected, I would either dump some output to a TextView on the display or I'd start the emulator in debugging mode and set breakpoints around the areas that I thought might be potentially responsible for the issues. At one point, when I was working on setting the user-level "Enable SMS" switch, the application would crash. The culprit ended up being that I had inadverantly flipped the column order when attempting to retrieve a user record from the database and map it to the UserModel that the application used.

## Considering the full app design and development process, from initial planning to finalization, where did you have to innovate to overcome a challenge?

I think the biggest requirement that caught me off guard and caused me quite a bit of grief to find the best way to work around was the "Delete All from this row" button in the grid. I worked through probably close to a dozen variants of my grid display before settling where I finally did. I think my final grid display is pretty cleanly built, but I thrashed pretty heavily to get there.

## In what specific component from your mobile app were you particularly successful in demonstrating your knowledge, skills, and experience?

I think one of the bigger solutions I pulled from my experience was the implementation of the `BaseActivity`. It allowed to me to control some global concerns, such as authorization to each activity or navigation between activities, in a centralized and consistent manner. It prevented me from having to rewrite a lot of code and created reliability of those pieces of functionality that it handled and reduced some testing as well.