# Remix OS - Desktop Android Experience

>Many a thief is a better man than many a clergyman, and miles nearer to the gate of the kingdom.

> ~George MacDonald

I didn't realize that this project even existed until noticing Jide's flagship product, the "Remix Mini" on Amazon. This is a 5" Android device which has an HDMI out designed to serve as a desktop with keyboard and mouse. Besides this dedicated device, you can also download the Remix OS iso from [their website](http://www.jide.com).

I went ahead and tried this, having just gotten a fresh ssd in the mail. Assuming it's a standard linux bootable usb image, I used "win32diskimager" on a flash drive, put my new drive in my laptop, and booted from the flash drive. Unfortunately, installation is not as straightforward as that. While it boots to the flashdrive and gives some minimal feedback, the computer goes to a pulsating RemixOS logo and just hangs.

This is a pretty new project, so I will forgive them, but they need better documentation so early adopters don't get hung up. When you boot from a flashdrive, it actually tries to install Remix OS on the *flashdrive*, not the computer's hard drive. I actually found this out after getting it to actually work - with apps crashing left and right and system processes stalling out due to the slow read/write speeds of an everyday flash drive it's not recommended.

What you're actually supposed to do is use their Windows only utility to create a partition on the drive you're currently using - after restarting your system will go to a grub menu with a choice to boot to Windows or Remix OS and it will work perfectly. I guess this is the scenario they're anticipating.

# Dual Booting Remix OS With Ubuntu

As I discovered, you can set up a dual boot alongside Ubuntu as well, which is what I was trying to do. This isn't explained anywhere on Jide's website, however, it should be, it's fantastic. I had to piece together how this is done by trolling xda-developers and watching youtube videos - reminds me of when I installed cyanogenmod on my Nook HD, Jide should provide some formal instructions for this so it doesn't feel like a hack.

First you need extract the contents of the iso into a dedicated directory, which I called "/remix". The file "system.sfs" needs to be extracted. This is actually a file-system, and you can "unsquash" it with the following command.

<pre id="code"><code class="language-javascript">unsquashfs system.sfs</code></pre>

That was kind of neat to learn about, I don't think I've ever seen that file type before. It produces the system.img file which you'll need for your grub menu entry.

It's necessary to add a empty directory called "data" along with the iso's files.

The difficult part was adding the menu entry to the grub2 menu. It needs to be just right. I noticed that some of the provided solutions had syntactical errors which caused the command to fail.

To edit the grub2 config, run the command below.

<pre id="code"><code class="language-javascript">sudo nano /etc/grub.d/40_custom</code></pre>

Beneath the comment section of the file, add the entry below. Like I said, I saw people using variations of this command, but this is the one that worked for me.

<pre id="code"><code class="language-javascript">menuentry 'Remix OS' --class android-x86 {
        insmod part_gpt
        search --file --no-floppy --set=root /remix/system.img
        linux /remix/kernel root=/dev/ram0 androidboot.hardware=remix_x86_64 androidboot.selinux=permissive CMDLINE
        initrd /remix/initrd.img
}" lang="js"></code></pre>

The file where you can alter how much time is given to interact with the grub2 menu can be changed in the file below.

<pre id="code"><code class="language-javascript">sudo nano /etc/default/grub" lang="js"></code></pre>

I change the HIDDEN_TIMEOUT to 10, I thought that might've affected my ability to see it or not, in any case, it's an important grub2 config file, so I thought I'd mention it.

After changing the grub2 settings, you need to update grub.

<pre id="code"><code class="language-javascript">sudo update grub</code></pre>

I couldn't get my grub2 menu to come up automatically, it was necessary for me to trigger it with the escape key (I read that the shift key is supposed to trigger it as well, which didn't work for me).

# The Experience

Remix OS is a collaboration between Jibe and the open-source and more low key [Android x86 project](http://www.android-x86.org). The installation is quick, provided you're doing this the easy way by using the Windows only partition tool provided with the iso, or if you followed the "hacker" tutorial above to get it to run from the grub2 menu.

You can get up and running very quickly after activating the Google Play store, and I had zero issues with hardware detection and use of the laptop touch screen. I tested [Persist](https://play.google.com/store/apps/details?id=com.adventureislands.persist), a game created in Stencyl by [Adventure Islands](http://www.stencyl.com/users/index/4413), and [Alto's Adventure](https://play.google.com/store/apps/details?id=com.noodlecake.altosadventure), created in Unity. It's stunning how perfectly these games play in full screen, I was blown away how natural it feels.

I installed [Marvin](https://play.google.com/store/apps/details?id=cz.dejvice.rc.Marvin) and [Speccy](https://play.google.com/store/apps/details?id=com.fms.speccy), two amazing ZX Spectrum emulators and found that they worked flawlessly. Most apps launch in a window that can be dragged around the desktop and resized. I noticed that switching between full screen and windowed appears to reload the app.

I experimented with the [Android Processing IDE](https://play.google.com/store/apps/details?id=com.calsignlabs.apde) and found that it wasn't able to run the sketches. This app ordinarily compiles an apk on the spot and installs it, here it just fails.

Opengl ES is 100% functional and I was stunned that even in the projects early stage it's as stable and performant as it is.

I was impressed to find that it's possible to install php, python, or nodejs using apt-get from the terminal. It's a total mystery how pure an Android environment this and how much "padding" Remix OS is providing to make this actually work, but from my first impression I can say that it's totally ready to use.

Remix OS is a really incredible project that is presently undermining Google's control of the Android environment. The founders are ex-Google employees, and it's surprising that this is legal at all. Remix OS makes some pretty bold statements in a short video you'll find in the movies directory, claiming that 

> At Jide, we believe the future of computing is Android, and we aspire to usher in a new era of exploration, transformation, and inspiration, the world has never seen before.

They include a quote at the end from Alan Kay of Xerox PARC who created the Smalltalk language.

> The past has already been written, and we are here to write the future.

> ~ Alan Kay

Though I was really happy with how this ended up working, I'm still disappointed that Jide isn't providing any information to people trying to get the OS installed, because was immediately obvious to me that anyone who is not trying to dual boot with Windows using the Windows only partition tool had to go straight to the XDA developers forums.

That's where you go for Android roms and rooting instructions - Remix OS is clearly a more sophisticated project that should't have anything to do with that.

Nonetheless, Google Play Store and Android app support is still forthcoming for Chromebooks, and it's seems clear that the experience will be exactly the same as what Remix OS is currently providing.