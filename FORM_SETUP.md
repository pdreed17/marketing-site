# Connecting the Waitlist Form to ConvertKit

## Step 1: Create ConvertKit Account

1. Go to https://convertkit.com (free up to 1,000 subscribers)
2. Create an account
3. Verify your email

## Step 2: Create a Form in ConvertKit

1. Go to "Grow" → "Landing Pages & Forms"
2. Click "Create New" → "Form"
3. Choose "Inline" form type
4. Design doesn't matter (we're using our own HTML)
5. Add fields:
   - Email (required, already there)
   - First Name (add custom field)
   - Role/Specialty (add custom field, dropdown)
6. Save the form

## Step 3: Get Your Form ID

1. Click on your form
2. Go to "Settings" → "Script embed"
3. Look for the form action URL, like:
   `https://app.convertkit.com/forms/1234567/subscriptions`
4. Note the form ID (1234567 in this example)

## Step 4: Update the Landing Page

Open `public/index.html` and find this section near the bottom:

```javascript
// Here you would send to your email service (ConvertKit, Buttondown, etc.)
console.log('Form submitted:', data);
```

Replace with:

```javascript
// Send to ConvertKit
fetch('https://app.convertkit.com/forms/YOUR_FORM_ID/subscriptions', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({
    email_address: data.email,
    fields: {
      first_name: data.name,
      specialty: data.role
    }
  })
})
.then(response => {
  if (!response.ok) throw new Error('Signup failed');
  console.log('Signup successful');
})
.catch(error => {
  console.error('Error:', error);
  alert('Something went wrong. Please try again.');
});
```

Replace `YOUR_FORM_ID` with your actual form ID.

## Step 5: Set Up Welcome Email

1. In ConvertKit, go to "Automate" → "Visual Automations"
2. Create new automation
3. Trigger: "Joins a form" → select your waitlist form
4. Add action: "Send email"
5. Write your welcome email (see 1-Page Marketing Plan, Square 4)
6. Attach your lead magnet PDF
7. Activate the automation

## Step 6: Test It

1. Deploy the updated landing page
2. Submit a test signup with your email
3. Verify:
   - You appear in ConvertKit subscribers
   - You receive the welcome email
   - The lead magnet is attached

---

## Alternative: Buttondown (Simpler)

If ConvertKit feels complex, Buttondown is simpler:

1. Sign up at https://buttondown.email (free up to 100 subscribers)
2. Get your API key from Settings
3. Use their API to submit:

```javascript
fetch('https://api.buttondown.email/v1/subscribers', {
  method: 'POST',
  headers: {
    'Authorization': 'Token YOUR_API_KEY',
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({
    email: data.email,
    metadata: {
      name: data.name,
      specialty: data.role
    }
  })
})
```

---

## Security Note

For production, you should use a serverless function (Vercel Edge Function) to hide your API key. But for early-stage waitlist collection, this direct approach works fine.
