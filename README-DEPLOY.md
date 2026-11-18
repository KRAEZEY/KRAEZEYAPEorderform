# KRAEZEYAPE combined storefront + order form

Upload these files to the **storefront-development** branch of KRAEZEY/KRAEZEYAPEorderform. The existing root index.html is replaced by the new storefront; the uploaded order form is copied **unchanged** to order/index.html.

## Routes
- `/` new storefront
- `/order` and `/order/` existing order form (Vercel clean URLs)

## Important pre-launch checks
1. **Do not deploy to main or change DNS until tested.** Preview deployments for non-production branches require Vercel Git integration and branch preview settings.
2. Existing order form uses two images hosted at `kraezeyape.com/_assets/...`. Those may break when Canva is disconnected. Export these originals from Canva and host them in `assets/`, then change only their two URLs in `order/index.html`.
3. Check all Supabase dropdowns, cart, PayPal/Venmo payment, and confirmation emails in a controlled test. The original code uses $1/item and performs database writes and emails after PayPal capture; no payment flow has been verified in this package.
4. Existing HTML contains public browser-side integration identifiers (PayPal client ID, Supabase anon key, EmailJS IDs); review Supabase RLS and payment server-side verification before production use.
5. Existing repository may have other files (e.g. owner pages, serverless functions, configs). **Keep those existing files**; merge this package into the branch rather than deleting the repository contents. Inspect any existing vercel.json before replacing it.
