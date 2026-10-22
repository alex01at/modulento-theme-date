# Date

A site theme for [Modulento](https://github.com/alex01at/modulento): a warm,
romantic look in rose and coral. Built for the [dating
extension](https://github.com/alex01at/modulento-ext-dating).

Unlike Modulento's other site themes (Indigo, Audigo, Merchigo, Card), this
one brings no card partials for offers or providers - the dating extension
has neither a catalogue nor provider profiles to give a bespoke card
layout to. It does bring its own `layout/base.twig`, for a three-column
shell loosely in the shape of a social feed: a left nav rail, the page's
own content in the middle, and a small static widget on the right. Every
other page's markup - the account's settings tabs, the order pages, and
so on - still comes straight from the `default` theme, just rendered
inside that same three-column shell since all of them extend this layout.

A theme's stylesheet is never merged with another's, though: whichever
theme is active supplies the *only* stylesheet the site loads, for every
page, including the ones this theme does not override. So `assets/theme.css`
still has to be a complete stylesheet - every class any template on the
site actually uses, not just a handful of colour variables - with these
things of its own on top:

- **The colour palette**: every colour Modulento's `default` theme already
  uses is a CSS variable; the base rules below them are `default`'s own,
  carried over so the site keeps working, just recoloured.
- **The home page's content** (`home-layout.json`) and a handful of extra
  rules for it: a hero pitching the app with a soft gradient and a faint
  heart pattern, a numbered "how it works" section, and a pricing
  call-to-action - instead of the default theme's catalogue-shaped
  hero/categories/offers/providers blocks, which would otherwise sit empty
  on a dating install.
- **The three-column shell** (`layout/base.twig`, the grid rules for
  `.app-shell`/`.app-rail`/`.app-widget`): a nav rail of the account's own
  links (or login/register, logged out) on the left, and a small "new
  profiles are waiting" widget on the right, linking to the swipe queue.
  Below `68rem` the rails stack above and below the content instead of
  beside it. The widget's own wording is in `lang/de.php` and `lang/en.php`
  (keys starting `theme.widget.`), editable the same way any other
  theme's small chrome texts are - see "Changing the wording" below.

## Changing the wording

The right-rail widget's wording is in `lang/de.php` and `lang/en.php`, with
keys starting `theme.`. Do not edit them here - an update would replace
the file. Put your own wording into `lang/<language>.php` of the
installation:

```php
<?php

return [
    'theme.widget.text' => 'Schon wieder neue Leute in deiner Nähe.',
];
```

Like the rest of the home page, every block is edited in place
(**Administration → Home page**, or directly on the page itself when signed
in with that permission): click into a heading or text to change it, add
pictures, reorder or remove blocks, or add a new one.

The theme has a dark scheme. It follows the device, unless an account has
chosen "light" or "dark" in its own settings.

A logo uploaded under **Administration → Themes → Branding** replaces the
decorative mark and the site's name in the header and footer; a separate
logo for the dark scheme, where there is one, is swapped in by CSS. A
favicon and the description set under **Administration → Settings** are
linked and tagged (including Open Graph and Twitter tags) without any
further setup - both come from the `default` theme's own layout, which this
theme leaves untouched.

## Installing

In Modulento, open **Administration → Packages**, enter
`alex01at/modulento-theme-date` and install. Then choose "Date"
under **Administration → Themes**. New versions appear on the Packages page.

By hand: unpack a release into `themes/date/` of the installation.

## Design values

A fresh installation's accent colour (**Administration → Design**) is
Modulento's own neutral blue, not this theme's - that page always wins over
the theme's stylesheet, by design, so an operator can retune any theme
without editing files. To match the look this README describes, set the
accent to a rose such as `#d4245a`, ground `#fff8f8`, text `#2b1620`, and
the border radius to `8px`–`10px`.

## Releasing

Set `version` in `theme.json`, commit, then tag and push:

```
git tag v0.1.0 && git push origin v0.1.0
```

The workflow checks that tag and `theme.json` agree, builds
`modulento-theme-date-<version>.zip` with its SHA-256 and publishes both
as a GitHub Release.

## Licence

GPL-3.0-or-later, see `LICENSE`.
