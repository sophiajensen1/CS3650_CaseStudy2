# Annotated Code Snippets

These examples describe the intended website implementation.
These are specifications, not running code. 

## Accessible Field Error

The label identifies the field. The description connects its error message.
Set aria-invalid only when validation fails.

```html
<label for="email">Email address</label>
<input
  id="email"
  name="email"
  type="email"
  required
  aria-invalid="true"
  aria-describedby="email-error"
>
<p id="email-error">
  Enter an email address in the correct format, like jane@example.com.
</p>
```

## Loading Announcement

Keep this region in the page and update its text when loading begins.

```html
<div role="status" aria-live="polite" aria-atomic="true">
  Loading available times…
</div>
```


## Preventing Repeated Submission

Set the processing flag before starting the request.
The submit handler must check it before sending another request.

```javascript
let processing = false;

async function submitBooking() {
  if (processing) return;

  processing = true;

  try {
    await sendDemoBooking();
    showConfirmation();
  } catch {
    showBookingError();
  } finally {
    processing = false;
  }
}
```

The booking functions above represent application-specific logic.
