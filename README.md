<html>
<head>
    <title>Multiple Shade Selection for Zirconia Only</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 20px;
        }
        img {
            width: 500px; /* Increased logo size */
            margin-bottom: 10px;
        }
        h1 {
            font-size: 24px;
        }
        h3 {
            font-size: 16px;
            color: gray;
        }
        input {
            margin: 5px;
            padding: 5px;
        }
        button {
            padding: 8px 12px;
            background-color: #007bff;
            color: white;
            border: none;
            cursor: pointer;
        }
        button:hover {
            background-color: #0056b3;
        }
        p {
            font-weight: bold;
            margin-top: 15px;
        }
    </style>
</head>
<body>

    <!-- Company Logo -->
    <img src="OPI.jpeg" alt="Company Logo">

    <!-- Main Title and Subtitle -->
    <h1>Multiple Shade Selection for Zirconia Only</h1>
    <h3>Please input all shades provided on the prescription.</h3>

    <!-- Shade Input Form -->
    <label>Incisal Shade (RX): <input type="text" id="incisal"></label><br>
    <label>Body/Mid Shade: <input type="text" id="body"></label><br>
    <label>Gingival Shade: <input type="text" id="gingival"></label><br>
    <button onclick="displayShade()">Submit</button>

    <!-- Output Section -->
    <p>Selected Shade: <span id="output"></span></p>

    <script>
        // RX Shade to Puck Shade conversion mapping
        const shadeConversion = {
            "OM1": "OM1", "OM2": "OM2", "OM3": "OM3", "1M1": "OM3", "1M2": "A1",
            "2L1.5": "B1", "2L2.5": "B3", "2M1": "A1", "2M2": "A2", "2M3": "B3",
            "2R1.5": "A2", "2R2.5": "A3", "3L1.5": "C2", "3L2.5": "B3", "3M1": "D2",
            "3M2": "D3", "3M3": "A3.5", "3R1.5": "D2", "3R2.5": "A3.5", "4L1.5": "C3",
            "4L2.5": "A3.5", "4M1": "D3", "4M2": "A3.5", "4M3": "A4", "4R1.5": "C3",
            "4R2.5": "A4", "5M1": "C4", "5M2": "A4", "5M3": "A4", "010": "OM1",
            "020": "OM2", "030": "OM3", "040": "OM3", "BL1": "OM1", "BL2": "OM2",
            "BL3": "OM3", "BL4": "OM3"
        };

        function displayShade() {
            // Get input values
            let incisalShade = document.getElementById("incisal").value.trim().toUpperCase();
            let bodyShade = document.getElementById("body").value.trim().toUpperCase();

            // Convert RX shade to Puck shade if found in conversion dictionary
            let convertedShade = shadeConversion[incisalShade] || incisalShade;

            // If incisal shade is empty, use body shade; if both are empty, show default message
            let finalShade = convertedShade && convertedShade !== "" ? convertedShade : (bodyShade !== "" ? bodyShade : "No shade entered");

            // Display the selected shade
            document.getElementById("output").innerText = finalShade;
        }
    </script>

</body>
</html>
-Shade-Selection
