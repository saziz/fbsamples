# ReactNative - Code Lab

In this code lab, we'll build a simple app that shows some information from
Github, using the Github api.

Helpful links:

* [docs](https://facebook.github.io/react-native/docs/getting-started.html)
* [movies example](https://github.com/facebook/react-native/tree/master/Examples/Movies)

## Step 1

- setup a new project `react-native init CodeLab`
- now let's start with a simple [list view](https://facebook.github.io/react-native/docs/listview.html) component (RepositoryList).

* don't forget the imports (copy from `index.android.js`)
* we are intentionally separating iOS and Android for now due to navigation.
  for now, let's modify ios and Android to show our RepositoryList. don't
  forget require it `var RepositoryList = require('./RepositoryList.js')`

* build it for either iOS or Android:
  `react-native run-android` or `react-native run-ios`.

* apply some minor [styling](https://facebook.github.io/react-native/docs/style.html) to make things look decent.

## Step 2

* now that we have a list of repositories, let's figure out how to show a repository details screen when an item is clicked. in order to do this, our app needs some sort of navigation, so we can know where we are in the app, can jump back where we came from, and so on. let's add a [Navigator](https://facebook.github.io/react-native/docs/using-navigators.html).

* so now we've added a `Navigator`, but it doesn't do much for us yet. First, let's get a sense of where we are. there are two ways to do this - first is to use `NavigationBar`, and the second is to handle it differently depending on iOS and Android to get a more native feel. This means replacing `Navigator` with [NavigatorIOS](https://facebook.github.io/react-native/docs/navigatorios.html) on iOS, and placing a [ToolBarAndroid](https://facebook.github.io/react-native/docs/toolbarandroid.html) in Android.

* awesome, but now we still need to add some sort of second screen and a way to transition between the screens (and a press state to indicate that this item is tappable!) let's wrap our repository item with a [TouchableHighlight](https://facebook.github.io/react-native/docs/touchablehighlight.html).

* great, so now we have a pressed state - let's make a `RepositoryDetails` screen which we show when this is tapped.

* finally, let's support back on Android - both in terms of using `BackAndroid` to support a back button press, and by adding an up button of sorts to the Toolbar.

## Step 3

* Let's get some real data. we can use [fetch](https://facebook.github.io/react-native/docs/network.html) to accomplish this inside of a new function in `RepositoryList`. we can call this function in `componentDidMount`.
* whenever we do web calls, we should show some sort of loading indicator, so let's do that next. We can do this by having a variable in state for isLoading, and showing an `ActivityIndicator` when it's true and the list when it's false.
* now let's update the title to be the repository title, and pass the relevant repository information to RepositoryDetails.
* let's cache the results from the queries when we do them

## Bonus

Here are some ideas for extra things you can do:

* improve the ui (render the avatar url)
* improve the transition
* ripples on Android
* allow changing the username directly from within the app (ex a search bar). see the Movies app for an example of this.
