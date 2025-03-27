# Custom Endless Scroll/Lazy Load Listener attached to Recycle View

Latest stable version:

[![](https://jitpack.io/v/mikkelofficial7/android-endless-scroll.svg)](https://jitpack.io/#mikkelofficial7/android-endless-scroll)

1. Add this gradle in ```build.gradle(:app)``` :
```
dependencies {
   implementation 'com.github.mikkelofficial7:android-endless-scroll:v1.1'
}
 ```
or gradle.kts:
```
dependencies {
  implementation("com.github.mikkelofficial7:android-endless-scroll:v1.1")
}
 ```

2. Add it in your root settings.gradle at the end of repositories:
```
repositories {
  mavenCentral()
  maven { url 'https://jitpack.io' }
}
```
3. In your ```Activity``` or ```Fragment``` class, add this variable:
```
private var scrollListener: EndlessScrollListener? = null
```
and in ```onCreate()``` section, you can access it by:
```
val linearLayoutManager = LinearLayoutManager(context)

binding?.recycleView?.apply {
    layoutManager = linearLayoutManager
    adapter = YourCustomAdapter(context)
    .
    .
}

scrollListener = object : EndlessScrollListener(linearLayoutManager) {
    override fun onLoadMore(page: Int, totalItemsCount: Int, view: RecyclerView?) {
        // do other thing....
    }
}

binding?.recycleView?.addOnScrollListener(scrollListener as EndlessScrollListener)
```
