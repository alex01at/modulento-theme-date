# Date

A site theme for [Modulento](https://github.com/alex01at/modulento): a warm,
romantic look in rose and coral. Built for the [dating
extension](https://github.com/alex01at/modulento-ext-dating).

Unlike Modulento's other site themes (Indigo, Audigo, Merchigo, Card), this
one is deliberately palette-only. Those themes each bring their own layout,
home page and card partials for offers and providers, because the apps they
are built for actually have those - a shop lists products, an auction
lists lots. The dating extension has neither: no catalogue, no provider
profiles, nothing to sell. So Date changes exactly two things:

- **The home page's content** (`home-layout.json`): a hero pitching the app,
  a "how it works" section, and a pricing call-to-action - instead of the
  default theme's catalogue-shaped hero/categories/offers/providers blocks,
  which would otherwise sit empty on a dating install.
- **The colour palette** (`assets/theme.css`): every colour Modulento's
  `default` theme already uses is a CSS variable: this theme only replaces
  their values. Every page - home, swipe, matches, chat, the account pages,
  even the administration's own templates it does not touch - therefore
  already looks like Date, with no template overrides at all.

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
