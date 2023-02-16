# The Court Says, Don’t Use Google Fonts

At the end of January this year, a regional court in Munich, Germany, ordered an unidentified website operator to pay a €100 fine for violating the plaintiff’s right to privacy by sharing their IP address with Google via the company’s Fonts API.

The General Data Protection Regulation (GDPR) considers an IP address to be personal data, as it is technically possible to identify the individual associated with it — it’s irrelevant whether the website operator or Google actually did so.

> “The defendant’s unauthorized disclosure of the plaintiff’s dynamic IP address to Google constitutes a violation of the general right of privacy in the form of the right of informational self-determination \[…\] includes the right of the individual to determine the disclosure and use of their personal data.”

The assets included in Google Fonts are available as part of a public repository on GitHub. An [issue opened](https://github.com/google/fonts/issues/1495) back on March 18, 2018, titled “ **GDPR Compliance** ”, questioned the company’s official position regarding the then-soon-to-be-implemented privacy policy change in the EU and EEA.

While users didn’t feel that the matter was resolved, the discussion has been closed since April 20, 2018, soon after Google issued a statement. According to [Google’s FAQ](https://developers.google.com/fonts/faq#what_does_using_the_google_fonts_api_mean_for_the_privacy_of_my_users), the Fonts API doesn’t collect any authenticated credentials used by “other Google services” and “No cookies are sent by website visitors.”

### Fine of up to €250,000

Apparently, that’s not good enough; the verdict stated, “The defendant violated the plaintiff’s right to informational self-determination by forwarding their dynamic IP address to Google when they accessed the website.”

In other words, as soon as the plaintiff opened the website, their browser sent a request to Google’s servers to download the font and display it on the page, consequently disclosing their IP — the user did not authorize this procedure.

According to [BuiltWith.com Technology Trends data](https://trends.builtwith.com/websitelist/Google-Font-API/Germany), the Google Fonts API is used by more than 50 million websites worldwide, with an estimated 870,589 websites across Germany.

While this case is partly a lesson for all to see, currently carrying a symbolic fine, the ruling states that website operators risk a fine of up to €250,000 for each violation, or up to six months in prison.

---

Breaching the GDPR, violating users’ privacy, and facing either hefty fines or actual jail time are not the only reasons to avoid Google Fonts. Even if the company isn’t tracking users across the web or storing explicitly private details, there are other detriments to using its service.

Let’s review the technical aspects of using Google Fonts as your font library:

* **HTTP requests** — whenever you fetch one or more font files from Google, you perform additional HTTP requests to `fonts.googleapis.com` (for the CSS file) and `fonts.gstatic.com` (for the font files). That means multiple round-trips for the DNS lookup, TCP connection, TLS negotiation, and the requested resource itself.
    
* **Caching**  — while the font files themselves are cached for one year, the CSS is only cached for 24 hours, so it can point to a newer version of the font file when it’s available. In reality, Google rarely updates fonts daily (and sometimes you [wouldn’t actually *WANT*](https://github.com/google/fonts/issues/1307) the updated version), causing a cycle of wasted resources.
    

Other changes and advancements in web technologies, including HTTP/2 and [cache partitioning](https://www.peakhour.io/blog/cache-partitioning-firefox-chrome/), have also [eliminated](https://www.stefanjudis.com/notes/say-goodbye-to-resource-caching-across-sites-and-domains/) some of the previous benefits of using third-party CDNs.

![Lighthouse performance metrics of a one-pager, showing better results when using local fonts](https://cdn-images-1.medium.com/max/1000/1*LZoFVafi8OnPbU3J_weu4g.png align="left")

![Summary of resources loaded in a one-pager, showing more requests for bigger files when using Google Fonts](https://cdn-images-1.medium.com/max/1000/1*DQvJTC0qaF0NPS3SREL0eg.png align="left")

*Comparing a one-pager performance (*[*PageSpeed Compare*](https://pagespeed.compare/)*)*

As performance expert Harry Roberts [wrote](https://csswizardry.com/2020/05/the-fastest-google-fonts/):

> “It’s widely accepted that self-hosted fonts are the fastest option: same-origin means reduced network negotiation, predictable URLs mean we can preload, self-hosted means we can set our own cache-control directives, and full ownership mitigates the risks that come with leaving static assets on third-party origins.”

### How-to: Loading Local Fonts

1. [Get the files](#1-get-the-files)
    
2. [Update the stylesheet](#2-update-the-stylesheet)
    

* [Tip: Fight FOUT](#fight-fout)
    
* [Tip: Subsetting](#subsetting)
    

1. [Preload](#3-preload)
    
2. [Cache](#4-cache)
    
3. [Security](#5-security)
    

* [Full snippet](#full-snippet)
    

So what can you do to avoid Google Fonts? Well, that’s what we’re here to show you, and may it please the court.

#### 1\. Get the files

When you download a file from Google Fonts, you get the `ttf` version, which you shouldn’t use on the web. The recommended format is `woff2`, supported by practically all browsers ([~97 percent](https://caniuse.com/?search=woff2)). There are several ways to obtain the `woff2`:

* Download the `ttf` and convert it using [CloudConvert](https://cloudconvert.com/ttf-to-woff2) or other similar services.
    
* Download the font file from the foundry/designer. For example, ***IBM Plex Sans***, used across **Project A** ’s website, is available for download from [IBM’s repository](https://github.com/IBM/plex).
    
* Download from Google Fonts:
    

1. Click on ***Select this style*** to add the weights you want.
    
2. Scroll to the bottom of the sidebar that slides from the right, and look for the code snippet.
    
3. Copy the link to the CSS file (not the links of the `preconnect`). E.g., `https://fonts.googleapis.com/css2?family=YOUR+FONT+NAME:wght@400&display=swap`.
    
4. From the list of `@font-face` declarations, copy the URL inside the src.
    
5. Paste it in the browser to generate a download link. E.g., `https://fonts.gstatic.com/s/YOUR_FONT_NAME/v13/zYX-KVElMYYaJe8bpLHnCwDKjbLuF6ZJW9XjDg.woff2.`
    
6. Save the font file(s).
    
7. Copy the files to your website’s **public folder**.
    

A less-convoluted way to obtain both the files and CSS is to use Mario Ranftl’s [google-webfont-helper](https://google-webfonts-helper.herokuapp.com/fonts), an open-source service that generates a ZIP file with customized font formats and a CSS snippet.  
This passion project is fantastic, but it hasn’t been updated in a few years and was inaccessible in the past.

#### 2\. Update the stylesheet

You can either adapt your existing stylesheet or choose the relevant `@font-face` declaration (probably *Latin glyphs*) from Google’s stylesheet, and copy it:

```css
@font-face {
  font-family: "IBM Plex Sans";
  font-style: normal;
  font-weight: 400;
  font-display: swap;
  src: url(path/to/font) format("woff2");
  unicode-range: U+0000–00FF, U+0131, U+0152–0153, U+02BB-02BC,
    U+02C6, U+02DA, U+02DC, U+2000–206F, U+2074, U+20AC, U+2122,
    U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD;
}
```

Update the `src` path according to the site’s directory structure.

#### Tip: Fight FOUT

Make sure that the `font-display` attribute doesn’t create the ***Flash of Unstyled Text (FOUT)***. One way to avoid it is to specify a fallback font (either a default [system fonts stack](https://css-tricks.com/snippets/css/system-font-stack/) or a typeface similar to the one you’re using).

Monica Dinculescu’s [Font Style Matcher](https://meowni.ca/font-style-matcher/) is a handy open-source tool designed to solve this: Scroll down Dinculescu’s site for a demonstration of the problem.

It’s important to note that besides being unpleasant, the jarring transition between the fonts causes layout shifts, measured as part of Google’s *Core Web Vitals*.

#### Tip: Subsetting

If you’re only using specific characters/glyphs and don’t need the whole typeface, you can further optimize the file size using an open-source [Python utility](https://github.com/zachleat/glyphhanger) or somewhat-hacky [manual](https://github.com/ironnysh/mighty#tips) method.

#### 3\. Preload

To improve performance and ensure the font file is available when the browser renders the CSS, preload it in advance. Add the following snippet to the `<head>`:

```html
<link rel="preload" href="/path/to/font.woff2" as="font" crossorigin="" />
```

#### 4\. Cache

You can cache fonts under the same policy as other static assets: E.g., `public, max-age=31536000, immutable`.

#### 5\. Security

If you have a Content Security Policy (CSP) response header in place, it’s now safe to remove the [font-src directive](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy/font-src) (i.e., `font-src https://fonts.gstatic.com;`)

Here’s the entire snippet:

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Loading Local Fonts</title>
    <link rel="preload" href="/path/to/font.woff2" as="font" crossorigin="" />
    <style>
        @font-face {
            font-family: "YOUR_FONT_FAMILY";
            font-style: normal;
            font-weight: 400;
            font-display: swap;
            src: url(path/to/font) format("woff2");
            unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD;
        }

        body {
            font-family: "YOUR_FONT_FAMILY", ui-sans-serif, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', system-ui, sans-serif;
        }
    </style>
</head>

<body>

</body>

</html>
```

---

[The Court Says, Don’t Use Google Fonts](https://insights.project-a.com/the-court-says-dont-use-google-fonts-7eb26765635b) was originally published on [Project A Insights](https://insights.project-a.com).