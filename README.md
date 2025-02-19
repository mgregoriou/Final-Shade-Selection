
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

    <!-- Company Logo (Ensure the file is in the same directory as index.html) -->
    <img src="OPI.jpeg" alt="Company Logo" onerror="this.onerror=null; this.src='default-logo.png';">

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
        // RX Shade to Puck Shade conversion mapping (Includes Incisal, Mid/Body, and Gingival)
        const shadeConversion = {
            // Vita Classic, Vita 3D Master, Bleach Shades
            "OM1": "OM1", "OM2": "OM2", "OM3": "OM3", "1M1": "OM3", "1M2": "A1",
            "2L1.5": "B1", "2L2.5": "B3", "2M1": "A1", "2M2": "A2", "2M3": "B3",
            "2R1.5": "A2", "2R2.5": "A3", "3L1.5": "C2", "3L2.5": "B3", "3M1": "D2",
            "3M2": "D3", "3M3": "A3.5", "3R1.5": "D2", "3R2.5": "A3.5", "4L1.5": "C3",
            "4L2.5": "A3.5", "4M1": "D3", "4M2": "A3.5", "4M3": "A4", "4R1.5": "C3",
            "4R2.5": "A4", "5M1": "C4", "5M2": "A4", "5M3": "A4", "010": "OM1",
            "020": "OM2", "030": "OM3", "040": "OM3", "BL1": "OM1", "BL2": "OM2",
            "BL3": "OM3", "BL4": "OM3",
            // Chromascope Shades
            "01/110": "A1", "1A/120": "A2", "2A/130": "A2", "1C/140": "A3", "2B/210": "A3",
            "1D/220": "A3", "1E/230": "A3", "2C/240": "A3.5", "3A/310": "B3", "5B/320": "B4",
            "2E/330": "B4", "3E/340": "A4", "4A/410": "D3", "6B/420": "C2", "4B/430": "C3",
            "6C/440": "C3", "6D/510": "C3", "4C/520": "C3", "3C/530": "A4", "4D/540": "A4",
            // Bioform Shades
            "B51": "A1", "B52": "B2", "B53": "A2", "B54": "A3", "B55": "B3",
            "B56": "A3", "B59": "A1", "B62": "A1", "B63": "A2", "B65": "A3",
            "B66": "A2", "B67": "B3", "B69": "D4", "B77": "C2", "B81": "C3",
            "B83": "A3.5", "B84": "A4", "B85": "B4", "B91": "C1", "B92": "D2",
            "B94": "C2", "B95": "C2", "B96": "C4"
        };

        function displayShade() {
            // Get input values
            let incisalShade = document.getElementById("incisal").value.trim().toUpperCase();
            let bodyShade = document.getElementById("body").value.trim().toUpperCase();
            let gingivalShade = document.getElementById("gingival").value.trim().toUpperCase();

            console.log("Input Incisal Shade:", incisalShade);
            console.log("Input Body Shade:", bodyShade);
            console.log("Input Gingival Shade:", gingivalShade);

            // Convert RX shades to Puck shades
            let convertedIncisal = shadeConversion[incisalShade] || (incisalShade !== "" ? incisalShade : "");
            let convertedBody = shadeConversion[bodyShade] || (bodyShade !== "" ? bodyShade : "");
            let convertedGingival = shadeConversion[gingivalShade] || (gingivalShade !== "" ? gingivalShade : "");

            console.log("Converted Incisal Shade:", convertedIncisal);
            console.log("Converted Body Shade:", convertedBody);
            console.log("Converted Gingival Shade:", convertedGingival);

            // Final shade logic:
            let finalShade;
            if (convertedIncisal !== "") {
                finalShade = convertedIncisal;  // Use converted incisal shade if available
            } else if (convertedBody !== "") {
                finalShade = convertedBody;  // If no incisal, use converted mid/body shade
            } else if (convertedGingival !== "") {
                finalShade = convertedGingival;  // If no incisal/mid, use converted gingival shade
            } else {
                finalShade = "No shade entered";  // If all are empty
            }

            console.log("Final Selected Shade:", finalShade);

            // Display the selected shade
            document.getElementById("output").innerText = finalShade;
        }
    </script>

</body>
</html>
