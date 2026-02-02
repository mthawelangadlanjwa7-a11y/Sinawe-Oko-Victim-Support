<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Victim Support Intake Form</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f5f7fa;
      margin: 0;
      padding: 20px;
    }
    .container {
      max-width: 700px;
      margin: auto;
      background: #fff;
      padding: 20px;
      border-radius: 8px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
    }
    h2 {
      text-align: center;
      color: #333;
    }
    label {
      display: block;
      margin-top: 15px;
      font-weight: bold;
    }
    input, select, textarea {
      width: 100%;
      padding: 10px;
      margin-top: 5px;
      border: 1px solid #ccc;
      border-radius: 5px;
    }
    .checkbox-group {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 10px;
      margin-top: 10px;
    }
    .checkbox-group label {
      font-weight: normal;
    }
    button {
      margin-top: 20px;
      padding: 12px;
      background: #0077cc;
      color: #fff;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      width: 100%;
    }
    button:hover {
      background: #005fa3;
    }
    .plan {
      margin-top: 20px;
      padding: 15px;
      background: #e8f4ff;
      border-radius: 5px;
      display: none;
    }
  </style>
</head>
<body>
  <div class="container">
    <h2>Victim Support Intake Form</h2>
    
    <label>Name (optional):</label>
    <input type="text" id="name">

    <label>Contact Number (optional):</label>
    <input type="text" id="contact">

    <label>Type of Abuse (tick all that apply):</label>
    <div class="checkbox-group">
      <label><input type="checkbox" value="Domestic Violence"> Domestic Violence</label>
      <label><input type="checkbox" value="Physical Abuse"> Physical Abuse</label>
      <label><input type="checkbox" value="Emotional Abuse"> Emotional Abuse</label>
      <label><input type="checkbox" value="Financial Abuse"> Financial Abuse</label>
      <label><input type="checkbox" value="Intimidation/Harassment"> Intimidation/Harassment</label>
      <label><input type="checkbox" value="Abduction/Forced Marriage"> Abduction/Forced Marriage</label>
      <label><input type="checkbox" value="Gender-Based Violence"> Gender-Based Violence</label>
      <label><input type="checkbox" value="Human Trafficking"> Human Trafficking</label>
      <label><input type="checkbox" value="Other"> Other Social Problem</label>
    </div>

    <label>Do you know the perpetrator?</label>
    <select id="perpetrator">
      <option value="">Select...</option>
      <option value="Yes">Yes</option>
      <option value="No">No</option>
    </select>

    <label>Have you been threatened after the incident?</label>
    <textarea id="threats" rows="3"></textarea>

    <label>How do you want us to assist you?</label>
    <textarea id="assistance" rows="3"></textarea>

    <button onclick="generatePlan()">Submit</button>

    <div class="plan" id="plan">
      <h3>Suggested Plan of Action</h3>
      <p id="planText"></p>
    </div>
  </div>

  <script>
    function generatePlan() {
      const abuses = Array.from(document.querySelectorAll('.checkbox-group input:checked'))
                          .map(cb => cb.value);
      const assistance = document.getElementById('assistance').value;

      let planMessage = "Based on your input, here are suggested steps:\n\n";

      if (abuses.includes("Domestic Violence") || abuses.includes("Physical Abuse")) {
        planMessage += "- Contact local shelters or hotlines for immediate safety.\n";
      }
      if (abuses.includes("Financial Abuse")) {
        planMessage += "- Seek financial counseling or legal aid for resource access.\n";
      }
      if (abuses.includes("Human Trafficking")) {
        planMessage += "- Reach out to specialized anti-trafficking organizations.\n";
      }
      if (assistance) {
        planMessage += `\nYou requested: "${assistance}". We will prioritize this in support planning.`;
      }

      document.getElementById('planText').innerText = planMessage;
      document.getElementById('plan').style.display = "block";
    }
  </script>
</body>
</html>
