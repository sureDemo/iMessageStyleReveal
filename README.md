Purpose
--------------

I recently needed to build the iMessage style pull-to-reveal timestamps feature for a personal project and decided to open source the implementation.


Installation
--------------

This project is now a Swift framework. So simply add

`pod 'SPXRevealableView'` -- Podfile

Then import using

`import RevealableCell` -- Swift
`@import RevealableCell` -- ObjC

at the top of your source file(s).


Usage
-------

In order to use RevealableCell in your application, follow the steps below:

1. Your cell must be a subclass of RevealableTableViewCell
2. You must register a nib or a RevealableView subclass using:

   `tableView.registerNib(nib, forRevealableViewReuseIdentifier: "identifier")` or
   `tableView.registerClass(revealableViewClass, forRevealableViewReuseIdentifier: "identifier")`
   
3. In `cellForRowAtIndexPath` you can dequeue and configure an instance using:

   ```swift
   if let view = tableView.dequeueReusableRevealableViewWithIdentifier("identifier") as? MyRevealableView {
     view.titleLabel.text = "" // configure
     cell.setRevealableView(view, style: .Slide, direction: .Left)
   }
   ```
    
This new implementation, provides reusable views of the same type as well as allowing you to have
different styles or directions for individual cells. 
    
Run this project, to see a demo similar to the iMessage app on your iOS device.

Additional Info
-------

RevealableViews also support AutoLayout now, so if you've setup your constraints correctly, the views will auto-size their widths (per cell) for you. However, you can also specify a fixed width for each cell using

`cell.revealableView.width = 100`

Note: The height will always be the same as the cell and the position is based on the `.style` of the `RevealableView`

Feel free to use in any way you see fit. Please try and reference me somewhere in your app if you use this in a production app and maybe even tell me about it via Twitter [@shaps](http://twitter.com/shaps) ;)


![Screenshot](http://shaps.me/assets/img/blog/iMessageStyleReveal.jpg)

Supported OS & SDK Versions
-----------------------------

* Supported build target - iOS 8.0
* Earliest supported deployment target - iOS 8.0
