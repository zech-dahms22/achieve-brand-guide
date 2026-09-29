# Achieve Brand Guide

Static site for the Achieve brand guide and logo library. No build step.

- `index.html` is the whole guide.
- `logos/` holds every official logo PNG, sorted by brand, plus a zip per brand and one zip of everything.

## Deploy on Vercel

1. Push this folder to a GitHub repo (for example `achieve-brand-guide`).
2. In Vercel, click Add New Project, import the repo, leave Framework Preset as Other, and deploy.
3. Add a domain under Project Settings, Domains (for example `brand.achievenet.org`) and add the CNAME Vercel gives you at your DNS provider.

## Updating logos

Drop the new PNG into the right folder under `logos/`, add a line for it in the `groups` list at the bottom of `index.html`, rebuild the zips, and push.

Rebuild zips from inside `logos/`:

```
rm -f achieve-logos-all.zip */*.zip
zip -r achieve-logos-all.zip .
for d in */; do n=${d%/}; z=achieve-$n-logos.zip; [ "$n" = achieve ] && z=achieve-masterbrand-logos.zip; zip -r "$n/$z" "$d"; done
```
