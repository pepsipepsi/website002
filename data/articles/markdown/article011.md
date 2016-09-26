# Android Apps Are Going To Run On Chromebooks

> Simplicity is the ultimate sophistication.

> ~ Leonardo da Vinci

Well, it's finally occurred, something I've been waiting years for. Some Chromebooks can [run Android apps now.](http://www.pcworld.com/article/3096784/computers/early-android-app-support-rolls-out-to-two-more-chromebooks.html) This, while still currently only supported on 3 specific Chromebook models, is going to be expanded to include a longer [list of models in the near future.](http://www.chromium.org/chromium-os/chrome-os-systems-supporting-android-apps) While I'm sure this is going to be a good selling point for Chromebooks, what I see this as is a significant expansion of the Android operating system.

This makes a compelling case for just targeting Android instead of nw.js or electron for your cross platform mobile friendly application or game. As a developer, you'll be able to develop towards a desktop experience on Android, no longer locked down to the touch only and small display factors that shape a lot of app's designs. As a consumer, you may be more compelled to screencast your Android device to a desktop monitor and use a bluetooth keyboard in the future than look for a Windows port for something.

For mobile gaming, this could be huge. Touch, while a quirky and intuitive input method, has some huge shortcomings in comparison with tactile buttons. The limitations of the audience has dictated trends in Android app design, but this new channel into the Google Play store for keyboard equipped devices could provide just enough incentive for game designers to expect a wider range of input. 

I've considered the benefits of targeting opengl-es over what mesa offers on Ubuntu before, and this further cements the practicality of that idea.

Chromebooks are already very interesting devices, and I've had two of them. I couldn't believe the utility of the Acer c710, at only $129 new, I had a replaceable full SATA hard drive, a replaceable battery, and an HD display.

I upgraded to a Acer c720 which has a 10 hour battery life, weighs less, and instead of the full SATA it has a replaceable M.2 SATA, the coolest, smallest, and most compact SSD I have ever seen. I don't understand why these are not more popular. Even in the Chromebook marketplace, it's far more common for devices to have memory soldered in, which I'm bewildered by.

And people install linux on Chromebooks. The easiest way is by installing chroots using [Crouton scripts ](https://github.com/dnschneid/crouton)- full Ubuntu or Debian installations running from jails alongside Chrome-os which you can switch in and out of on the fly. Somewhat more involved is installing linux as the primary os, which requires the removal of a metallic sticker which serves as a write protect on the motherboard. Other challenges to booting directly to linux are the touchpad and display drivers, which are included in many dedicated distros, such as [Cub Linux](https://cublinux.com/).

People even install Windows on some Chromebooks, which I don't know anything about, but I can't imagine a compelling reason besides price for someone to try to do that. There's plenty of laptops designed specifically to run Windows, and Chromebooks are intended to run linux. Between Android phones and Chromebooks, this is the widest commercial proliferation of unix based systems in history, and it's completely appropriate. For an operating system conceived by Bell labs, the telephone company, it's not surprising that the main use cases for these computers are phone calls, sms, internet, and casual gaming. The theme is networking.

Many have noted the limitations of Chrome-os not being Windows and hence not having the proprietary Microsoft runtime that fewer and fewer consumers are clinging to as they get older. Unsurprisingly, schools are buying up Chromebooks. Development targeting Chromebooks is simplified, it's platform is nw.js, formerly known as webkit. It's Google Chrome with C++ bindings for os specific functionality, like memory management, accessing the system tray, the camera, file operations etc. Apps developed targeting nw.js can be run cross-platform, or run in a web-browser without installing anything - it's an open runtime, the opposite of proprietary.

What if there was a run-time that Google owned that was still cross platform, but would only run naively on their own devices? What if they could roll this out on inexpensive machines that most people already have? That's Android. You can't run Android apps on Windows or Mac, but now you can on Chromebooks - I think there could be a compelling reason for people to upgrade to Chrome-os from Windows in the near future.