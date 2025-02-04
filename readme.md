# phamminhdao.com

## Infomation

Using available theme template on: https://startbootstrap.com/theme/creative 

## Data storage

Form submission recorded in google sheets: https://docs.google.com/spreadsheets/d/1BA0WeysblJN8NWDgdWyleLn9278IqkUwP1Zj0eBVKmc

javascript script for data submission
```javascript
<script>
  document.addEventListener("DOMContentLoaded", function () {
    document
      .getElementById("contactForm")
      .addEventListener("submit", function (event) {
        event.preventDefault();

        var formData = {
          name: document.getElementById("name").value,
          email: document.getElementById("email").value,
          phone: document.getElementById("phone").value,
          message: document.getElementById("message").value,
        };

        fetch(
          "https://script.google.com/macros/s/AKfycbzmU7fzQA4WtLGYv68uRG3X_1KAUm20tVFF0dX29whczrqf2HSPD1WZoWiFDvtgvMs/exec",
          {
            method: "POST",
            body: JSON.stringify(formData),
            headers: { "Content-Type": "application/json" },
            mode: "no-cors",
          }
        )
          .then((response) => console.log("Success:", response))
          .catch((error) => console.error("Error:", error));

        document.getElementById("submitSuccessMessage").classList.remove("d-none");
        document.getElementById("submitButton").classList.add("disabled");
        document.getElementById("email").setAttribute("disabled", "true");
        document.getElementById("name").setAttribute("disabled", "true");
        document.getElementById("phone").setAttribute("disabled", "true");
        document.getElementById("message").setAttribute("disabled", "true");
      });
  });
</script>
```

## Deployment

Deployment using firebase hosting: https://firebase.google.com/docs/hosting/quickstart

Download firebase cli if it does not available (MacOS)
```
curl -sL https://firebase.tools | bash
```

Login to firebase by internet explorer
```
firebase login
```

Make a deployment
```
firebase deploy --only hosting:pham-minh-dao
```
