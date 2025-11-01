10X Media — Static Marketing Site

This is a lightweight static website for 10X Media: a social media marketing agency.

Contents:
- index.html: site markup
- css/styles.css: styles
- js/script.js: small interactions (counters, mobile nav, form submit)

How to use:
1. Open `index.html` in your browser. No build step required.
Optional preview with a simple HTTP server (Python 3):

```powershell
python -m http.server 8000 --directory .
# then open http://localhost:8000 in your browser
```

Tailwind production build (recommended):

1. Install dependencies (requires Node.js & npm):

```powershell
npm install
```

2. Build the CSS once:

```powershell
npm run build:css
```

3. For development, run the watcher:

```powershell
npm run watch:css
```

The Tailwind-built CSS will output to `css/styles.css`. `index-tailwind.html` is already configured to use this file.

Formspree integration:

- The contact form in `index-tailwind.html` is set to POST to Formspree. Replace `https://formspree.io/f/your-form-id` with your Formspree form endpoint. See https://formspree.io for setup.

EmailJS client-side integration (optional):

- This project includes an optional EmailJS client integration so you can send emails directly from the browser without a custom server. To enable it:
  1. Sign up at https://www.emailjs.com and create a Service (e.g., Gmail) and an Email Template.
  2. In the EmailJS dashboard note your Service ID (e.g., `service_xxx`), Template ID (e.g., `template_yyy`), and Public Key (user ID).
  3. In `index.html` the EmailJS SDK is included and initialized with a placeholder key. Replace the placeholder in the inline script near the contact form:

	  - Replace `YOUR_EMAILJS_USER_ID` with your EmailJS public key.

  4. Configure the form element to include the service and template ids, for example:

	  <form id="contact-form" data-emailjs-service="service_xxx" data-emailjs-template="template_yyy" action="https://formspree.io/f/your-form-id">

  5. The client-side JS in `js/script.js` will prefer EmailJS (when available) and fall back to Formspree or a simulated submission if EmailJS isn't configured.

Testing locally:

- For quick local testing, the site uses a simulated send when no backend is configured. To test EmailJS specifically, ensure you replace the placeholders and try submitting the form while viewing the page over `http://localhost:8000` (or a hosted URL). EmailJS may require public access or specific provider settings for third-party email providers.

Next steps / improvements:
- Add real analytics and tracking
- Hook contact form to email provider or send via server
- Replace placeholders with real brand assets and photos
- Add more case study pages and downloadable PDFs

Verification performed:
- Opened and inspected `index.html`, `css/styles.css`, and `js/script.js` to ensure files saved correctly.
- Added reveal-on-scroll and a basic testimonial carousel.

If you'd like, I can also:
- Replace placeholder text with your brand copy and images
- Connect the contact form to an email service or serverless function
- Produce an optimized export for hosting (Netlify/Vercel)
