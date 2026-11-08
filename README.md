# Pawsitive Rescuers website

The one-page website for Pawsitive Rescuers, Palmetto Bluff, SC.

## What's in this folder

| File / folder | What it is |
|---|---|
| `index.html` | The whole website: text, layout, links and styling. |
| `images/` | All the photos and the logo, one file per photo. |
| `.nojekyll` | An empty file that tells GitHub to serve the site exactly as-is. Leave it in. (It is a hidden file, so you may not see it on a Mac or PC. That's fine.) |
| `README.md` | This guide. |

The site has no build step and no special software. Everything lives in `index.html` plus the `images` folder, and you can open `index.html` in any browser to preview it.

---

## 1. Put the site on GitHub Pages (free hosting)

### A. Create a GitHub account and repository

1. Go to **github.com** and sign up. Consider using a shared club email (see section 4) so the account isn't tied to one volunteer.
2. Click the **+** in the top-right corner, then **New repository**.
3. Name it `pawsitive-rescuers` (or anything you like). Set it to **Public**. GitHub Pages is free for public repositories.
4. Leave the other boxes unchecked and click **Create repository**.

### B. Upload the files

1. Unzip `pawsitive-rescuers-site.zip` on your computer.
2. In your new repository, click the link that says **uploading an existing file**.
3. Open the unzipped `pawsitive-rescuers-site` folder and drag **everything inside it** (`index.html`, `README.md` and the whole `images` folder) into the browser window.
   - Drag the files that are *inside* the folder, not the folder itself, so `index.html` ends up at the top level of the repository.
   - The `.nojekyll` file is hidden and may not get dragged. The site works without it. If you want it, click **Add file → Create new file**, name it `.nojekyll`, leave it empty and commit.
4. Scroll down and click **Commit changes**.

### C. Turn on GitHub Pages

1. In the repository, go to **Settings → Pages** (under "Code and automation" in the left sidebar).
2. Under **Build and deployment → Source**, choose **Deploy from a branch**.
3. Choose branch **main**, folder **/ (root)**, and click **Save**.
4. Wait a minute or two, then refresh. GitHub shows your live address, like `https://YOUR-USERNAME.github.io/pawsitive-rescuers/`.

### D. Connect a custom domain (for example, pawsitiverescuers.org)

1. **Buy the domain** from a registrar such as Cloudflare, Porkbun, Namecheap or Squarespace Domains. A `.org` suits a charitable group well.
2. **Tell GitHub first.** In **Settings → Pages → Custom domain**, type the domain (for example `pawsitiverescuers.org`) and click **Save**. Do this before changing DNS. GitHub warns that pointing DNS at GitHub without adding the domain here first could let someone else host a site on it.
3. **Add DNS records** at your registrar:

   | Type | Host / Name | Value |
   |---|---|---|
   | A | `@` | `185.199.108.153` |
   | A | `@` | `185.199.109.153` |
   | A | `@` | `185.199.110.153` |
   | A | `@` | `185.199.111.153` |
   | CNAME | `www` | `YOUR-USERNAME.github.io` |

   Delete any "parking page" or default A records the registrar added for `@`. **Don't touch MX records.** Those are for email (section 4).
4. **Wait.** DNS can take up to 24 hours to propagate, though it's usually much faster.
5. **Turn on HTTPS.** Back in **Settings → Pages**, tick **Enforce HTTPS** once it becomes available.
6. **Optional but recommended: verify the domain.** In your GitHub *account* settings (not the repository), go to **Settings → Pages → Add a domain**. GitHub gives you a TXT record to add at your registrar. Verifying protects the domain from takeover.

### E. Making changes later

- **Edit text:** open `index.html` on GitHub, click the pencil icon, make your change and click **Commit changes**. The live site updates in about a minute.
- **Add a photo:**
  1. Upload the photo into the `images` folder (**Add file → Upload files**). Use a short name with no spaces, like `adoption-day-2027.jpg`. Resize big phone photos to about 1600 px wide first.
  2. In `index.html`, find the line `<!-- ADD NEW PHOTOS ABOVE THIS LINE -->`. Paste this just *below* it (new photos appear first), then change the file name, the description and the caption:

     ```html
     <figure><button type="button" class="ph" aria-label="Enlarge photo: Your caption"><img src="images/your-photo.jpg" alt="Describe what's in the photo for screen-reader users." loading="lazy"></button><figcaption>Your caption</figcaption></figure>
     ```

- **Update the save-the-date:** search `index.html` for `October 27, 2027`. It appears in the top banner and in the Events list.

---

## 2. Current donation setup (no changes needed)

The **Donate** button currently goes to the Pawsitive Rescuers Fund page at the Community Foundation of the Lowcountry (CFL):

`https://lowcountry.fcsuite.com/erp/donate/create/fund?funit_id=5026`

That link works on GitHub Pages as-is, and CFL issues the tax receipts. Zeffy (next section) is optional.

---

## 3. Zeffy integration (optional)

[Zeffy](https://www.zeffy.com) is free donation and event-ticketing software for nonprofits. Instead of charging fees, it asks donors for an optional tip to Zeffy at checkout. It's especially handy for selling **Cocktails for a Cause tickets and raffle tickets**.

### Step 0: Talk to the Community Foundation first ⚠️

Pawsitive Rescuers is a fund housed at CFL. It isn't a separate nonprofit with its own EIN. Zeffy accepts fiscally sponsored groups, but:

- the Zeffy account must be **created in the sponsor's name** (CFL's name appears on the tax receipts), and
- you verify it with **the sponsor's EIN and IRS SS-4 form**.

So before signing up, ask CFL:
1. Do they allow funds to use Zeffy, and will they give you their EIN and SS-4?
2. **Which bank account should Zeffy pay out to?** Zeffy's guide says a sponsored group can connect its *own* bank account. A CFL fund usually doesn't have one, and CFL may require all gifts to go straight to them. Get the answer in writing.

If CFL says no, keep using the CFL donate link. For ticketed events, ask CFL what they recommend.

### Step 1: Create the Zeffy form

1. Sign up at zeffy.com using the details CFL approves.
2. Under **Settings → Visual identity**, upload `images/logo.png`.
3. Create a **Donation form** (or a **Ticketing** form for the event). Use the site's colors if you like: teal `#0e6672` and coral `#ee8559`.

### Step 2: Add it to the website (pick one option)

**Option A: Simple link (easiest).** In Zeffy, click **Share** next to the form and copy the form link. In `index.html`, find the Donate button:

```html
<a class="btn coral" href="https://lowcountry.fcsuite.com/erp/donate/create/fund?funit_id=5026" ...>Donate</a>
```

Replace the `https://lowcountry...5026` address with your Zeffy link. Keep the quotation marks.

**Option B: Embed the form on the page.** In Zeffy, go to **Share → Embed on your website → Form** and copy the HTML code. In `index.html`, search for `ZEFFY (optional)`. A placeholder comment sits right below the Donate button. Paste the Zeffy code just below that comment. Zeffy's code looks roughly like this:

```html
<div style="position:relative;overflow:hidden;height:1200px;width:100%;">
  <iframe title="Donation form powered by Zeffy"
    style="position:absolute;border:0;top:0;left:0;bottom:0;right:0;width:100%;height:100%"
    src="https://www.zeffy.com/embed/donation-form/YOUR-FORM-ID"
    allowpaymentrequest allowTransparency="true"></iframe>
</div>
```

Raise or lower `height:1200px` until the form has no scroll bar. You can then delete the old Donate button if it's no longer needed.

**Option C: Pop-up button.** In Zeffy's share options, choose **Embed a pop-up form**. Zeffy gives you two snippets. Paste the button code where the Donate button is. Paste the header script into `index.html` just before `</head>`.

For events, you can link a "Buy tickets" button in the Events section the same way as Option A.

---

## 4. Getting a custom-domain email address (for example, hello@pawsitiverescuers.org)

**Important:** **Google Workspace for Nonprofits (free Gmail on your domain) is not available to you.** Google doesn't accept fiscally sponsored groups that lack their own 501(c)(3) status, and Pawsitive Rescuers is a fund at CFL. Here are the options that do work, best first:

### ⭐ Recommended: Zoho Mail "Forever Free" plan

- **Cost:** $0 for up to 5 mailboxes on one domain, with 5 GB each.
- **Limits:** you can only use it through the Zoho website and the Zoho Mail phone app. It won't connect to Outlook, Apple Mail or the Gmail app; that requires Zoho's inexpensive paid "Mail Lite" plan. Adding a 6th user means the whole organization moves to a paid plan.
- **Why it fits:** a small volunteer club needs only a few shared addresses, such as `hello@`, `events@` and `donate@`.

**Setup:**
1. Buy your domain first (section 1D).
2. Go to zoho.com/mail → Pricing → **Forever Free Plan → Sign up**. (It's at the bottom of the pricing page.)
3. Enter your domain. Zoho asks you to add a **TXT record** at your registrar to prove you own it.
4. Create your mailboxes (for example `hello@pawsitiverescuers.org`).
5. Add the **MX**, **SPF (TXT)** and **DKIM (TXT)** records Zoho gives you at your registrar. These sit alongside the GitHub A/CNAME records without conflicting.
6. Install the Zoho Mail app on your phone.

### Alternative: free forwarding to your existing Gmail

If volunteers would rather keep using their own inboxes, use a forwarding service. **Cloudflare Email Routing** is free if your domain uses Cloudflare. ImprovMX is another option. Mail sent to `hello@pawsitiverescuers.org` lands in a personal Gmail. Replying *from* the club address takes extra setup ("Send mail as" in Gmail), and forwarding is less tidy when volunteers change.

### Paid option: Google Workspace Business Starter

You get full Gmail on your domain, with Google Drive and Calendar. It's the most familiar option, but it's billed per user per month. Pick it only if the club wants to pay for the Google experience.

### Tips
- Use **one shared address** for the GitHub, Zeffy, domain-registrar and social-media accounts. That way, nothing is lost when a volunteer steps down. Keep the passwords in a shared password manager.
- Turn on **two-factor authentication** for GitHub, the registrar and the email account.
- Add the new email address to the site's footer or Join section once it's working.

---

## Quick checklist

- [ ] Create GitHub account (with the club email, if it's ready)
- [ ] Create repository and upload the files
- [ ] Turn on GitHub Pages and confirm the site loads at `…github.io/…`
- [ ] Buy the domain
- [ ] Add the custom domain in GitHub, then the DNS records, then Enforce HTTPS
- [ ] Set up Zoho Mail (TXT, MX, SPF, DKIM records)
- [ ] Ask CFL about Zeffy before signing up
- [ ] Add the Zeffy link or embed, if approved

*Information about GitHub, Zeffy, Google and Zoho was checked in November 2026. These services change their plans from time to time, so double-check anything that matters before you rely on it.*
