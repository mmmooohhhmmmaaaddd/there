<!DOCTYPE html>

<html>
<head>
  <meta http-equiv="CONTENT-TYPE" content="text/html; charset=UTF-8">
  <title>Hello, World!</title>
</head>
<body>
  <h1>
    Hello, World!
  </h1>
</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Visitor Registration Form</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            padding: 20px;
        }
        .container {
            max-width: 400px;
            margin: auto;
            background: white;
            padding: 20px;
            border-radius: 5px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
        }
        h2 {
            text-align: center;
        }
        .form-group {
            margin-bottom: 15px;
        }
        label {
            display: block;
            margin-bottom: 5px;
        }
        input[type="text"], input[type="tel"], input[type="number"], select {
            width: 100%;
            padding: 8px;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
        button {
            width: 100%;
            padding: 10px;
            background-color: #5cb85c;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
        button:hover {
            background-color: #4cae4c;
        }
    </style>
</head>
<body>

<div class="container">
    <h2>Visitor Registration</h2>
    <form id="visitorForm">
        <div class="form-group">
            <label for="fullName">Full Name</label>
            <input type="text" id="fullName" name="fullName" required>
        </div>
        <div class="form-group">
            <label for="phoneNumber">Phone Number</label>
            <input type="tel" id="phoneNumber" name="phoneNumber" required>
        </div>
        <div class="form-group">
            <label for="passportNumber">Passport Number</label>
            <input type="number" id="passportNumber" name="passportNumber" required>
        </div>
        <div class="form-group">
            <label for="gender">Gender</label>
            <select id="gender" name="gender" required>
                <option value="Male">Male</option>
                <option value="Female">Female</option>
            </select>
        </div>
        <div class="form-group">
            <label for="reasonVisit">Reason for Visit</label>
            <input type="text" id="reasonVisit" name="reasonVisit" required>
        </div>
        <button type="submit">Submit</button>
    </form>
</div>

<script>
    document.querySelector("#visitorForm").addEventListener("submit", function(event) {
        event.preventDefault();
        const formData = new FormData(this);
        const data = {
            fullName: formData.get("fullName"),
            phoneNumber: formData.get("phoneNumber"),
            passportNumber: formData.get("passportNumber"),
            gender: formData.get("gender"),
            reasonVisit: formData.get("reasonVisit")
        };
        
        fetch("https://script.google.com/macros/s/AKfycbxKaRRTdPiCNxFHWpHpL_QNvaXZsR0-7gsE9VTOATcm/dev", {
            method: "POST",
            body: JSON.stringify(data),
            headers: {
                "Content-Type": "application/json"
            }
        })
        .then(response => response.json())
        .then(data => {
            alert("Data submitted successfully!");
        })
        .catch(error => {
            alert("An error occurred while submitting the data.");
        });
    });
</script>

</body>
</html>
