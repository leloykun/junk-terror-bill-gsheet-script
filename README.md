# Junk Terror Bill GSheet Script
A GSheet script that can be used to automatically send emails to your congressmen 

## Script:
```javascript
function sendEmails() {
  var sheet = SpreadsheetApp.getActiveSheet();
  var startRow = 8;     // First row of data to process
  var numRows = 312;    // Number of rows to process
  // Fetch the range of cells A1:B100
  var dataRange = sheet.getRange(startRow, 1, numRows, 100)
  // Fetch values for each row in the Range.
  var data = dataRange.getValues();
  for (i in data) {
    var row = data[i];
    var name = row[1];            // change the row #s 
    var emailAddress = row[2];    // if necessary

    var message = "Dear " + name + ",<br><br>Junk Terror Bill Now";
    var subject = "Junk Terror Bill Now";

    MailApp.sendEmail(emailAddress, subject, message, {
      htmlBody: message
    });
  }
}
```

## How to use it:
1) Open a Gsheets file containing the names and email addresses of your congressmen
2) Click Tools -> Script Editor
3) Copy-paste the script there
4) Click Send
