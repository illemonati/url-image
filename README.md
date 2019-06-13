# URLImage

`URLImage` is a SwiftUI view that displays an image downloaded from provided URL. `URLImage` manages downloading remote image and caching it locally, both in memory and on disk, for you.

Creating `URLImage` view is described in my blog post [URL Image view in SwiftUI](https://medium.com/@dmytro.anokhin/url-image-view-in-swiftui-f08f85d942d8).

There's also a demo app [URLImageApp](https://github.com/dmytro-anokhin/url-image-app).

## Installation

`URLImage` is a Swift Package and you can install it with Xcode 11:
- Copy SSH `git@github.com:dmytro-anokhin/url-image.git` or HTTPS `https://github.com/dmytro-anokhin/url-image.git` URL from github;
- Open **File/Swift Packages/Add Package Dependency...** in Xcode 11;
- Paste the URL and follow steps.

## Usage

 `URLImage` must be initialized with a URL and optional placeholder image.
 
 ```swift
let url: URL = // ...

URLImage(url)

URLImage(url, placeholder: Image(systemName: "photo"))
``` 

Using in a view:

```swift
import SwiftUI
import URLImage

struct MyView : View {

    let url: URL

    var body: some View {
        URLImage(url)
    }
}
```

Using in a list:

```swift
import SwiftUI
import URLImage

struct MyListView : View {

    let urls: [URL]

    var body: some View {
        List(urls.identified(by: \.self)) { url in
            HStack {
                URLImage(url)
                    .frame(minWidth: 100.0, maxWidth: 100.0, minHeight: 100.0, maxHeight: 100.0)
                    .clipped()
                Text("\(url)")
            }
        }
    }
}
```