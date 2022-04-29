# Building Accessible Websites

When building in Webflow, we aim to make sure all of the best practices are accounted for just as we would if we were building the site using traditional front-end tools.

Webflow makes a point of flagging any problems when publishing the site, however we’ll also explain how you can use Lighthouse to test the accessibility score of your whole site and spot any not so obvious issues you may have missed.

Webflow also gives you a handy [checklist](https://webflow.com/accessibility/checklist) that you can use, but to give you a headstart we’ve covered the main accessibility points we look for first.

## Headings

### The importance of headings

Headings create structure in the webpage by specifying the content hierarchy. A hero heading for example will most likely be the primary heading, or `H1`, with each subsequent section of the page being introduced with a secondary heading, or `H2` (And so on).

Heading sizes range from `1` through to `6`, and you can easily choose between these sizes in Webflow using the settings panel on the right. Making sure the correct heading tag is applied will go a long way in making your site more easy to digest for assistive technologies.

### Order of headings

This heading hierarchy should also be sequential as well. If you have a `H2` to introduce a featured blog section for example, then the blog card headings would need to be a `H3` as they are the next heading in the page structure.

If you do skip a heading level, users of screen readers may think they’ve missed a section if the content jumps between headings in no logical order.

Webflow will flag this and tell you if a heading level is skipped, but it’s worth understanding why this is important.

[https://www.w3.org/WAI/tutorials/page-structure/headings/](https://www.w3.org/WAI/tutorials/page-structure/headings/)

## Landmarks

### The importance of landmarks

Not only do landmarks make your layers and sections easier to follow for yourself, but they also go a long way in helping assistive technologies such as screen readers scan the structure of the page and navigate the content much more quickly.

The most common landmarks or regions we use on our sites are:

`nav` : Navigation/Navbar

`main` : Page Content

`header` : Hero/Intro

`section` Page Section

`footer` : Footer (Sits outside the `main` tag)

### Choosing a landmark

To change the HTML tag for an element, you can go into the settings panel on the right and choose the specific tag. These aren’t actually flagged as an issue in Webflow, however it is something to be mindful of when building each page.

_A lot of these tags are obvious, however if you find you’re unsure if a specific tag is needed, it’s better to leave it as a `div`. If you use these tags in the wrong way, you may inadvertently make the content less accessible._

[https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles/landmark_role](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles/landmark_role)

## Colour

### Getting the right contrast

Colour plays an important role in design, so it is crucial that the contrast ratio is high enough for all users, regardless of any constraints with their vision or device.

The contrast ratio is the perceived brightness or luminance between two colours. Text on a coloured background is one of the most common issues where contrast fails, however this contrast ratio also applies to other elements such as images, icons and buttons.

You can easily check the contrast ratio as early as Figma with the help of various plug-ins found in the community, and there is also a contrast checker built directly into Webflow’s colour selector that tells you whether an element has a suitable ratio or not.

Ideally, you should be shooting for a minimum ratio score of `AA` on all elements, however the size of the element will also determine the contrast ratio. This means a colour may pass the accessibility test on large text, but fail when used on smaller text.

### Using colour with other visual elements

Another thing to be mindful of is making sure you aren’t using colour alone to convey information. With error messages for example, using an accompanying error icon means that people that may have issues distinguishing reds will still be able to understand at a glance that an error has occurred.

[https://webaim.org/resources/contrastchecker/](https://webaim.org/resources/contrastchecker/)

[https://webaim.org/articles/contrast/](https://webaim.org/articles/contrast/)

## Links

### Making your links clear

Links are a common and important item in websites. Whether they’re navigation links, buttons or inline hyperlinks, their sole purpose is to get the user from one place to another. By asking the user to click on something, we must provide them with enough trust and clarity so that they don’t feel unsure as to what to expect once they click on the link.

In order to avoid any ambiguity, make sure to label the link as clearly and concisely as possible. Avoid generic “Click here” or “Read more” labels unless the context of the link is clear (Such as under some additional information like in a hero section).

### Labelling non-descriptive links

For links that don’t have any label such as social icons, you can use an additional ARIA attribute called `aria-label`.

Webflow supports custom attributes, so in the link settings you can add the following:

`aria-label="Description of the link"`

By adding this, any link without a visible label will still be clearly interpreted by screen readers meaning you won’t end up with empty links that users may miss.

[https://usability.yale.edu/web-accessibility/articles/links](https://usability.yale.edu/web-accessibility/articles/links)

## Images

### Adding descriptions

Images are great for bringing a bit more visual interest to a page. Despite being visual, the content of an image should still be accessible to people using assistive technologies, and so we always aim to include descriptive snippets of text (alternative text) where possible.

Webflow not only flags any missing alt text, but they make it really easy for you to find the image and resolve the problem.

When adding a description, make it as detailed as is reasonably possible by explaining what the photo consists of or what the context of the image is (Who’s in it? What are they doing?).

You don’t have to include a description for every image though, as sometimes an image might be a background shape or something that is purely decorative and not important to the content. If this is the case, you can use an empty alt tag by making the description decorative instead.

Another advantage of using more informative alt text is the SEO benefit, and increasing your chances of ranking higher in Google and other search engines.

### Choosing the right format

The image type and size can also play a big role in the performance and accessibility of your site. Large images will of course take longer to load, which may cause issues for users without a strong internet connection.

When it comes to file type, we recommend using the following formats based on the type of image you are using:

`JPG` For standard images that don’t have a transparent background. Although PNGs are higher quality, JPGs are smaller in size and don't take up as much of the load time.

`PNG` For images with a transparent background. Great for mockups or other assets such as image collages.

`SVG` These are good for vector graphics and icons as they are scalable and also smaller in file size than if you were to save them as a PNG.

`WEBP` This isn’t supported by Webflow (yet), but they’re still worth mentioning as they are the most [optimised file type](https://developers.google.com/speed/webp/docs/webp_study) for images on the web.

### Optimising images

Once you’ve exported your imagery, depending on the original file size and export quality, you may find your images are fairly big. The bigger the image; the more data that has to be loaded.

Webflow has a max file size of `4MB`, however it gives you a warning if the image file exceeds a size as low as `100KB`. You don’t have to aim for this, however be mindful of it and try to keep your images as small as possible.

One thing we always do is run our images through a compression tool specific to that file type. There are plenty of free tools available, and they are great for lossless compression meaning your image quality isn’t affected.

Our go-to tools are:

**JPG:** [https://tinyjpg.com/](https://tinyjpg.com/)

**PNG:** [https://tinypng.com/](https://tinypng.com/)

**SVG:** [https://jakearchibald.github.io/svgomg/](https://jakearchibald.github.io/svgomg/)

By stripping out all of the excess data in your images/assets, those percentages eventually add up to give you a much better performing website as a whole.

### Keeping text separate

Text is meant to be read, but if that text is part of an image and the user can’t see it, it’ll be missed. That’s why we always try to avoid using text images and instead aim to include a caption, description, or written breakdown if the image is a chart or graph for example.

By keeping all of the text as separate HTML tags, you won’t be excluding parts of the content from any of your users.

### Organising your assets

This one is more for us, but making sure your images are properly named and organised will go a long way in helping us find/replace them as the project grows.

Not only that, but a well named image means that if you absolutely need to, you can use the asset name as the fallback alt text instead. Not only will this help you score accessibility points, but you’ll also contribute to your site's overall SEO performance.

[https://www.shopify.co.uk/blog/7412852-10-must-know-image-optimization-tips](https://www.shopify.co.uk/blog/7412852-10-must-know-image-optimization-tips)

[https://www.w3.org/WAI/tutorials/images/](https://www.w3.org/WAI/tutorials/images/)

## Lighthouse

Developed by Google, Lighthouse allows you to easily run an audit on your webpage and get a score out of 100 against four main metrics. When it comes to testing your sites performance, SEO and accessibility, Lighthouse is up there as one of the most useful tools (And it’s completely free).

Lighthouse works as a Chrome extension, and is available as either a pinned extension or as part of the inspect tool once installed. From there, it's just a case of clicking the “Generate report” link in order to run an audit.

Not only are the audits great for providing you with a score for each metric, but they also give a detailed breakdown of where the issues are occurring along with useful resources to help you research and solve the problem.

<aside>
💡 Don’t get hung up on trying to get a perfect score. When it comes to auditing a Webflow site, there will inevitably be issues that are out of your control due to the backend processes and hosting that is handled entirely by Webflow.
</aside>

[https://developers.google.com/web/tools/lighthouse](https://developers.google.com/web/tools/lighthouse)
