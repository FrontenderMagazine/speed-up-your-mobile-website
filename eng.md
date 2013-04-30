# Speed Up Your Mobile Website

Performance is important on all sites, but on a mobile device, it is even more
important. They have slower connections and less processing power than your
computer or laptop. This already means a longer wait to see and interact with
the content of a website. To further my point on web performance, check out this
article on how it could affect your [bottom line](http://blog.kissmetrics.com
/loading-time/). Below I go through a few methods to speed up your mobile site
and cut off some time from loading. Before you go ahead with any of these
methods, check out your current page load time at [pingdom][1].

*Just note that these methods are not all specific to mobile, but can be used 
for your full website as well as the mobile version.*

## Big, Fat Images

Images are a necessary evil of the web world, but they are a huge cause in long
load times on most websites. There are some good ways to mitigate this in a few
simple steps.

### Minimize Image Size

If you are re-sizing a 500×500 image to 50×50, this is a major problem. Your
browser will still have to load that high-resolution image, even though you are
only displaying it at 10% the original size. Make sure you re-size your images
as small as possible. If you are worried about retina screens, just make the
image twice as large as it will be displayed. So instead of using 500×500, use a
100×100 image and re-size it to 50×50 in CSS or HTML. I recommend Photoshop and
their [Save for Web & Devices][18] feature. Here is an online guide on how
to [save for the web][2].

### Use CSS3 Instead of Images

The fewer the images the better, so why not use some beautiful CSS3 effects to
make your website stick out? With border radius, box shadows, gradients, skews,
rotates and much more at your disposal, you should have no problem creating
complex effects in CSS. While it may not be possible to do all effects in CSS,
you should be looking to incorporate more into your designs to use this newer
technology. Check out below for some cool CSS3 resources.

* [10 of the coolest CSS3 effects][3]
* [One-div.com][4]
* [Fancy Input on TNW][5]
* [Advanced Hover Effects][6]

### Responsive Image Plugins

One of the larger problems with a responsive website is that large images have
to be scaled down to fit smaller screens. This is not very optimal for a mobile
device user who has to load a huge image that they will only get at 1/4 of the
size. [Responsive Img][7] is a great jQuery plugin that will actually swap out 
your images src at different breakpoints. This way you will not be loading 
large images on a responsive site, but rather smaller ones that will help 
improve you load times. Another one that could work for you without using a 
server-side script is [responsiveBreakpointJQ][8].

### Image Sprites

A good way to compact your images into one single image is using an image
sprite. Packing a large amount of images into one sprite can save quite a few
HTTP requests (more on that at the bottom).

![Social Sprite][Figure 1]

The sprite above is currently used on my site (the four images on top are hard
to see). There could be a total of eight image requests, or just one, with the
best choice being just one. It takes the browser a lot longer to issue out those
eight requests and load them, than just one request, even if the one request is
a larger size. For some more advantages, check out this article on 
[Design Review][9].

A large drawback of image sprites is that they cannot be responsive (not that I
know of anyway). These usually work best for smaller, more static images. I
would highly recommend creating your [own sprites][10] and not using a tool 
that generates them for you.

## Put Your Files On A Diet

The next thing that can drastically affect your load times is the amount of
external CSS and JavaScript you are loading. Make sure to have as few files as
possible and merge them together when you can. There are a few other things you
can do to help with this though.

### Minify CSS and JavaScript

Minification is getting very popular among developers. You may have noticed the
unreadable mess when you look at a [jQuery file][11]. The beauty of doing this 
is that not only will your file be smaller, but your browser can actually 
execute minified JavaScript faster than one with white-space and longer 
variable names.

* [jscompress][12]
* [Online YUI Compressor][13]
* [CSS Minifier][14]

*Be careful when minimizing CSS files, as your Media Queries will get broken 
in some.*

### GZIP Files

GZIP is the same as zipping your files on your laptop to make them smaller. This
helps further reduce the size of your files and can be done to your HTML,
JavaScript, and your CSS. Your browser will download, unzip and then parse your
file, just like any other. Check out this conversation on [Stack Overflow][15] 
about doing it with .htaccess.

Not all hosts will allow GZIP on their servers. While it is handy, it has quite
a cost on CPU performance. Usually the better the hosting, the more options you
will have. I host through HostGator and they only allow GZIP on some of their
more expensive deals, but thanks to [Will Ray][16], I found out I can do 
[mod_deflate][17] instead, which is similar.

## Other Considerations

Here are a few more things you can do to help with performance and page load.

### Inline CSS and JavaScript

You always hear that you should separate your CSS and JavaScript by putting them
in external files. But have you ever thought the impact it could have on your
site rendering time? Let me explain.

When your browser is parsing your recently downloaded HTML document and
encounters an inline block of CSS or JavaScript, it will have to stop, switch
contexts, and then parse the inline block. This causes a massive slowdown in the
time it takes to render the page to the screen, also if the CSS affects an
element above it, the browser will have to re-render the screen. So do your
browser a big favor and externalize all CSS and JavaScript possible.

### HTTP Requests

Each image, CSS, and JavaScript file you include will be another HTTP request to
a server. Too many of these and the time it takes to download and parse each of
these could severely impact your load time. Merge your files together where you
can and just exclude CSS or scripts that you won’t need for that certain page.

Another quick tip is to spread out your HTTP requests between different hosts.
Browsers can only download between 4-6 files at a time from each host. So if you
split your requests between 4 different hosts you could download 16-24 separate
files at once.

## Conclusion

I hope these tips will help you decrease the load and rendering time of your
website. I use these tips myself every time I develop. Make sure to check the
increase in load time with [pingdom][1] after you are all finished up.

[1]: http://tools.pingdom.com/fpt/
[2]: http://sixrevisions.com/web_design/comprehensive-guide-saving-images-for-web/
[3]: http://www.webdesignerdepot.com/2012/03/10-of-the-coolest-css-css3-effects-10-of-the-coolest-css-css3-effects-10-of-the-coolest-css-and-css3-effects/
[4]: http://one-div.com/
[5]: http://thenextweb.com/dd/2013/02/21/fancy-input-adds-css3-text-effects-to-input-fields-a-gimmick-or-a-chance-to-delight/
[6]: http://codecanyon.net/item/advanced-css3-hover-effects-4/4143438
[7]: http://responsiveimg.com/
[8]: https://github.com/Designer023/responsiveBreakpointJQ
[9]: http://designreviver.com/tips/the-advantages-of-using-css-sprites-along-with-a-few-tips/
[10]: http://mysprit.es/tool
[11]: http://ajax.googleapis.com/ajax/libs/jquery/1.9.1/jquery.min.js
[12]: http://jscompress.com/
[13]: http://refresh-sf.com/yui/
[14]: http://www.cssminifier.com/
[15]: http://stackoverflow.com/questions/2666120/how-can-i-gzip-my-javascript-and-css-files
[16]: http://www.will-ray.com/
[17]: http://support.hostgator.com/articles/specialized-help/technical/apache-htaccess/mod_deflate
[18]: http://www.deke.com/content/photoshop-top-40-feature-34-save-web-and-devices

[Figure 1]: img/social-sprite.png