Motion CAPTCHA
A CAPTCHA whose letters exist only as motion. Screenshots, OCR, and static image models see only uniform noise, while human eyes can effortlessly read the letters through kinetic tracking.

We are currently testing this service on Velocity Wave Communications' edge infrastructure and are actively looking for developers to integrate it, try to break it, and provide feedback on its effectiveness against bots.

🧪 Call for Testers
We need your help to battle-test this concept. Please generate a key, drop the widget into a staging environment or side project, and let us know:

Bot Deflection: Does it effectively stop automated spam on your forms?

Browser Compatibility: Are there any rendering stutters on specific mobile devices or older browsers?

UX Feedback: How do your users find the experience compared to traditional puzzle CAPTCHAs?

🚀 Quick Start
Keys are free, instant, and require no signup. Head to captcha.velocitywave.co.uk to generate your sitekey and secret pair.

1. Frontend Integration
Place the widget inside your HTML <form>. When a visitor successfully solves the CAPTCHA, a hidden field named motion-captcha-response is automatically populated and submitted with your form.

HTML
<!-- Add the script to your page -->
<script src="https://captcha.velocitywave.co.uk/motion-captcha.js" async defer></script>

<!-- Place this inside your <form> element -->
<div class="motion-captcha" data-sitekey="YOUR_SITEKEY"></div>
2. Backend Verification
Before processing the form submission, verify the response token from your backend. The endpoint mimics the familiar reCAPTCHA siteverify shape, making it a drop-in replacement for many existing setups.

Request:

HTTP
POST https://captcha.velocitywave.co.uk/siteverify
Content-Type: application/x-www-form-urlencoded

secret=YOUR_SECRET&response=<value of motion-captcha-response>
Response (Success):

JSON
{
  "success": true, 
  "challenge_ts": "2026-09-18T03:44:28.000Z"
}
Response (Failure):

JSON
{
  "success": false, 
  "error-codes": ["timeout-or-duplicate"]
}
Note: Each response token is single-use and expires automatically after 5 minutes.

⚙️ Configuration & Customization
You can customize the widget's behavior and translate the UI by adding optional data attributes to the .motion-captcha div:

Lifecycle Hooks (For SPAs)

data-callback="fnName": Executes a global window function and passes the token once solved.

UI Translation Strings

data-label: Change the default instructions.

data-reload: Text for the reload/refresh button.

data-play: Text for the play button.

data-checking: Status text while verifying the answer.

data-verified: Status text upon successful solve.

data-wrong: Error text for an incorrect guess.

data-error: Error text for a network or system failure.

Rendering Adjustments

data-speed: Adjust the velocity of the moving particles.

data-density: Control the number of particles in the canvas.

data-size: Adjust the rendering scale of the canvas.

🤝 Accessibility Note
Because this CAPTCHA relies entirely on visual kinetic tracking, it is not accessible to screen readers or users with severe visual impairments. If you implement Motion CAPTCHA on a production site, please ensure you offer an alternative verification route (such as email loop verification or magic links).

🐛 Feedback & Bug Reports
If you manage to scrape the text programmatically, encounter a bug, or have a feature request, please open an issue in this repository.
