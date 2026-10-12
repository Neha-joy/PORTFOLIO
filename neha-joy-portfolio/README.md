# Neha Joy — React Portfolio

A modern, responsive, single-page portfolio website built with **React.js + JavaScript + Vite** based on the attached CV.

## Getting started

Requirements: Node.js 18+ (Node 20+ recommended), npm.

```bash
npm install
npm run dev
```

Open the local address printed in the terminal (normally http://localhost:5173).

## Build for production

```bash
npm run build
npm run preview
```

The deployable website is generated in `dist/`. Publish that folder to Netlify, Vercel, or another static host.

## Customize

- Change content, projects, experience, and skills in `src/main.jsx`.
- Change layout, colors, and typography in `src/style.css`.
- Replace `public/Neha_Joy_Resume.pdf` to update the downloadable resume.
- Add your GitHub, LinkedIn, and project links once you have confirmed URLs. They are intentionally not invented.
- The contact form sends through EmailJS after you configure your own EmailJS keys. A direct email link is still available as backup.

## Features

- Responsive sticky navigation and mobile menu
- Hero with animated coding card
- About, skills, filterable projects, experience, education, contact sections
- Downloadable original resume
- Click-to-email and copy-email buttons
- Lightweight CSS animations and accessible reduced-motion setting

## Enable the contact form (EmailJS)

The form fields are Name, Email, Subject, and Message. It displays sending, success, and error states. The form needs **your** EmailJS account configuration before it can deliver messages.

1. Register at https://www.emailjs.com/ and connect an email service (e.g., Gmail or Outlook) in **Email Services**.
2. In **Email Templates**, create a template with these variables:
   - **To Email**: `nehajoy002@gmail.com` (set this directly in the EmailJS template settings)
   - **Subject**: `Portfolio contact: {{subject}}`
   - **Body**:
     ```text
     Name: {{from_name}}
     Email: {{reply_to}}
     Subject: {{subject}}

     {{message}}
     ```
   - **Reply To**: `{{reply_to}}`
3. Copy **Service ID**, **Template ID**, and **Public Key** from EmailJS.
4. Copy `.env.example` to `.env.local` and replace placeholder values:
   ```env
   VITE_EMAILJS_SERVICE_ID=service_your_service
   VITE_EMAILJS_TEMPLATE_ID=template_your_template
   VITE_EMAILJS_PUBLIC_KEY=your_public_key
   ```
5. Restart `npm run dev`, submit a test message, and confirm it arrives at `nehajoy002@gmail.com`.
6. When deploying to Vercel or Netlify, set the same three variables in your site's environment-variable settings, then redeploy.

**Important**: Vite `VITE_` values are publicly visible in browser bundles, as designed for EmailJS public configuration. Do not put private keys or passwords here. Set EmailJS domain restrictions, rate limits and/or CAPTCHA protection in the EmailJS dashboard to reduce misuse. If the form is not configured, it clearly displays an error and visitors can use the direct email link.
