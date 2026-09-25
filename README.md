# apps.vibkings.com

The public site for Vibkings apps: one page per app, each with its own privacy policy, terms and
support contact. Google Play will not publish an app without a privacy policy at a public URL that
loads for anyone, and this is where it lives.

```
/                          all apps
/style.css                 one stylesheet for every page
/CNAME                     apps.vibkings.com — what GitHub Pages serves it as
/afterdark/                After Dark: Street War
/afterdark/privacy.html    ← this URL goes in Play Console
/afterdark/terms.html
```

**One folder per app.** The next app gets `/thatapp/` with the same three pages. Folders rather than
`afterdark-privacy.html` so nothing collides as the list grows, a new page can be added to one app
without renaming anything, and every page shares one stylesheet.

No frameworks, no fonts, no external requests. The pages work on a phone, follow the system's light
or dark theme, and load instantly on a slow connection — which matters, because a reviewer on a bad
connection who cannot load your privacy policy treats it as missing.

## Publishing it

1. Create a **new, public** GitHub repository — `vibkings-apps` is a reasonable name. Keep it separate
   from any app's source repository: this is a public website, the source is not.
2. Upload everything in this folder, keeping the structure. `CNAME` must be at the root.
3. **Settings ▸ Pages ▸ Source: Deploy from a branch**, branch `main`, folder `/ (root)`. Save.
4. GitHub reads `CNAME` and sets the custom domain to `apps.vibkings.com` by itself.
5. At whoever runs DNS for `vibkings.com`, add a **CNAME record**: name `apps`, value
   `vibkings.github.io` (no `https://`, no trailing dot needed in most panels).
6. Wait — usually minutes, sometimes an hour. Then in **Settings ▸ Pages**, tick **Enforce HTTPS**
   once the certificate has been issued. It cannot be ticked before that.
7. Open `https://apps.vibkings.com/afterdark/privacy.html` on a phone, in a browser with no account
   signed in, and confirm it loads.

Step 7 is the one that matters. A URL that only works for you is the same as no URL.

## Then in Play Console

- **Policy ▸ App content ▸ Privacy policy** → `https://apps.vibkings.com/afterdark/privacy.html`
- **Data deletion** → the same URL; section 7 of the policy carries the instructions.
- **Store listing ▸ Website** → `https://apps.vibkings.com/afterdark/`
- **Support email** → the address on the page.

## Keeping it honest

The documents also exist as Markdown in `../legal/`, which is easier to read and diff. Neither copy is
generated from the other, so **change both in the same commit, and change the "Last updated" date in
both.** A privacy policy that no longer matches what the app does is worse than none: it is a promise
to players and to Google that is then broken.

Update the pages when: an SDK is added or swapped, the app starts collecting something new, in-app
purchases go live, or the app reaches a country whose law adds a requirement.

## Once the game is on Google Play

Replace "Coming soon to Google Play" in `afterdark/index.html` with the store link:

```
https://play.google.com/store/apps/details?id=com.vibkingsglobal.afterdarkstreetwar
```

Do not put that link up before the listing is live — a broken store link on the page a reviewer
checks is an avoidable bad impression.

## The domain has to keep working

Once `apps.vibkings.com/afterdark/privacy.html` is filed with Google, it must stay reachable. If the
domain lapses or the subdomain is repointed, the policy 404s and the app can be suspended for it. Keep
`vibkings.com` on auto-renew, and do not reuse the `apps` subdomain for anything else.
