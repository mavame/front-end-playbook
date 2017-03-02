# Dynamit's Front-end Playbook

---

# Table of Contents

---

# Development Process

## Version Control

## DRY

## Code Commenting

# Performance

# SEO

Include a canonical url tag on each page. Use [trailing slashes](http://googlewebmastercentral.blogspot.com/2010/04/to-slash-or-not-to-slash.html) appropriately. Prefer `https` when available.

```html
<link rel="canonical" href="https://example.com/some-page" />
```

# Accessibility
## Visually Hide Text, But Allow Screen Readers to Read

```css
.visually-hidden {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip-path: rect(0,0,0,0);
  border: 0;
}
```

## Links 
- Avoid using ALL CAPS (even `text-transform: uppercase` can make it sound like a screen reader is yelling at you)
- Use visually hidden spans to add additonal context

```html
<!-- not much context -->
<a href="tel:18885555555">1-888-555-5555</a> 

<!-- text is hidden visually, but screen reader can read it -->
<a href="tel:18885555555"><span class="visually-hidden">For more information on XYZ Corp. call</span> 1-888-555-5555</a>
```

- Don't use URLs as only text
- When a link will do something unexpected, announce that to the user
- Don't use `target="_blank"` (confusing to the user, removes back button functionality)
- If `target="_blank"` must be used, inform the user they will be taken away from the site
- Font icon / SVG links need to have, at the very least, complimentary text that explains the link
- For internal actions, use `<button>`
- For taking users away from the current page, use `<a>`
- `<a>` must always have an `href` to pass testing
- Don't bother using [`title`](https://www.paciellogroup.com/blog/2012/01/html5-accessibility-chops-title-attribute-use-and-abuse/)

## Skip Links / Bypass Blocks

Coming Soon

## Visible Focus
- [WCAG 2.4.7](http://www.w3.org/TR/2012/NOTE-UNDERSTANDING-WCAG20-20120103/navigation-mechanisms-focus-visible.html) - Any keyboard operable user interface has a mode of operation where the keyboard focus indicator is visible. (Level AA)
- Never use `outline: none`
- Can update the outline so it looks different than default, but a visible border must be displayed
- Common failure is using `blur()` to take off focus, instead focus on another item
- Give your elements `:focus` wherever you have `:hover` in your CSS
- Focus needs to be taken into account when using `.hover()` 
- Typical failures occur for dropdown navigation not shown when the user focuses on a the top level menu item

## Images
- Always have alt text of some sort
```html
<!-- indicates the image is decorative and does not have text in the image -->
<img alt="" src="../.."> 

<!-- indicates the image is decorative and does not have text in the image -->
<img alt="This text should be descriptive/informative, but not repeat information that is already present" src="../.."> 
```
- `alt` text Should be kept under 125 characters
- Items like charts or maps that represent a lot of information, `<caption>` or `longdesc` should be used (example needed)
- GIFs should not have more than 3 flashes per second
- If possible, don't play GIF until hovered over
- Never use the filename as alt text 

## Headings
- [Use semantic markup and structure your page with one](http://adrianroselli.com/2013/12/the-truth-about-truth-about-multiple-h1.html) `<h1>` 
- Think of your page as the table of contents
- Turn off styling to test if the visual heirarchy makes sense
- Screen readers use headings as hot key points

## Color Contrast
- #000 on #fff background is not the best for readability and can [cause eye strain](http://ux.stackexchange.com/questions/53264/dark-or-white-color-theme-is-better-for-the-eyes)
- Ratio of 4.5:1 must be met for regular text
- 19px and bold is 3:1, 24px and basic color is 3:1
- Dyslexics do better with unique fonts (Comic Sans all characters are unique)
- Automated testing tools can't judge color contrast of text over an image
- Images with text in them need to have this contrast level and alt text equal to the text on the image
- [Testing color contrast] (http://jxnblk.com/colorable/demos/text/)

## Tab Order
- `tabindex="0"` and `tabindex="-1"` are all that should ever be used
- Never use `tabindex="1+"`
- Seriously. Don't.
- `tabindex="-1"` removes the element from the default tab order but allows you to focus on it programatically
- `tabindex="0"` places the element in the default tab order
- Proposal is in to deprecate any tab index that is greater than 0

## Form Elements
- All `<input>` must have `<label>` associated with them
- Note the `name` attribute does not have to match
```html
<label for="theinput">Input here:</label>
<input type="text" name="whatever" id="theinput">
```


## Random Tidbits
- Include a `lang=` attribute on the `<html>` tag
- Don't use `<meta name="viewport" content="user-scalable=no" />`. Users must be able to zoom
- Take into account that users should be able to go to zoom in to 200% and have the site still work