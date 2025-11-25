
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Plant Care Guide For Farmers: Pesticides, Soil, and Prices</title>
<style>
body { font-family: Arial, sans-serif; margin: 20px; background-color: #f4f4f4; }
h1 { color: #8A9A5B; }
select, button, input[type="file"] { padding: 10px; margin: 10px 0; }
.info { background: #8A9A5B; padding: 15px; border-radius: 10px; margin-top: 20px; color: white; }
ul { list-style-type: disc; padding-left: 20px; }
.disclaimer { color: #8A9A5B; font-weight: bold; }
.section { margin-bottom: 20px; }
</style>
</head>
<body>
<h1>Plant Care Guide For Farmers</h1>
<p>
Select a plant for pesticides, soil info, and market prices. 
<span class="disclaimer">Consult experts for application. Prices are approximate and vary.</span>
</p>
<p>
For more detailed plant care tips, visit 
<a href="https://github.com/darshanmhulagur-coder/plant-care-guid.git" target="_blank" rel="noopener noreferrer">Farmers World Plant Care</a>.
</p>
<!-- Plant selection dropdown -->
<label for="plant-select">Choose a plant:</label>
<select id="plant-select">
<option value="">Select</option>
<option value="tomato">Tomato</option>
<option value="rose">Rose</option>
<option value="corn">Corn</option>
<option value="green_leaf_lettuce">Green Leaf Lettuce</option>
<option value="green_chilly">Green Chilly</option>
<option value="onion">Onion</option>
<option value="broccoli">broccoli</option>
<option value="capcicum">capcicum</option>
</select>
<button onclick="showInfo()">Get Information</button>
<div id="plant-info" class="info" style="display: none;">
<div class="section">
<h2>Recommended Pesticides</h2>
<div id="pesticide-content"></div>
</div>
<div class="section">
<h2>Soil Recommendations</h2>
<div id="soil-content"></div>
</div>
<div class="section">
<h2>Market Prices</h2>
<div id="price-content"></div>
</div>
</div>
<script>
const plantData = {
  tomato: {
    pesticides: [
      { name: "Neem Oil", type: "Organic", use: "Controls aphids, mites. Spray diluted on leaves." },
      { name: "Copper Fungicide", type: "Chemical", use: "Fights blight. Apply as directed; avoid overuse." }
    ],
    soil: "Well-draining loamy soil with pH 6.0-6.8. Amend with compost for nutrients. Ensure good drainage to prevent root rot.",
    price: "Approx. ₹20-₹21 per kilogram (retail, varies by variety and season; wholesale)."
  },
  rose: {
    pesticides: [
      { name: "Insecticidal Soap", type: "Organic", use: "Kills aphids. Safe for beneficial insects." },
      { name: "Systemic Insecticide (e.g., Imidacloprid)", type: "Chemical", use: "For borers. Use sparingly to avoid soil harm." }
    ],
    soil: "Rich, well-draining soil with pH 6.0-7.0. Mix in organic matter like peat moss. Roses prefer slightly acidic conditions.",
    price: "Approx. ₹180 per kilogram (cut flowers; varies by grade and market)."
  },
  corn: {
    pesticides: [
      { name: "Bacillus thuringiensis (Bt)", type: "Organic", use: "Targets caterpillars. Environmentally friendly." },
      { name: "Glyphosate", type: "Chemical", use: "Weed control. Not for direct pest; check labels." }
    ],
    soil: "Fertile, well-draining loam with pH 6.0-7.0. High nitrogen content needed; test soil annually.",
    price: "Approx. ₹17.33-₹19.31 per kilogram (grain; wholesale futures vary; price varies daily)."
  },
  green_leaf_lettuce: {
    pesticides: [
      { name: "Diatomaceous Earth", type: "Organic", use: "Deters slugs. Sprinkle around plants." },
      { name: "Pyrethrin Spray", type: "Chemical", use: "For aphids. Quick-acting but may harm bees." }
    ],
    soil: "Moist, fertile sandy loam with pH 6.0-7.0. Keep soil consistently damp; avoid waterlogging.",
    price: "Approx. ₹80 per kilogram (head lettuce; organic varieties higher)."
  },
  green_chilly: {
    pesticides: [
      { name: "Imidacloprid", type: "Chemical", use: "For aphids, jassids, thrips. Quick-acting but may harm bees." },
      { name: "Pyriproxyfen", type: "Chemical", use: "For whiteflies." }
    ],
    soil: "Well-drained, loamy soil rich in organic matter with pH 6.0-7.5. Amend soil with compost or vermicompost; ensure good drainage to prevent root rot; fertilize appropriately.",
    price: "Approx. ₹30-32.5 per kilogram."
  },
  onion: {
    pesticides: [
      { name: "Dimethoate", type: "Chemical", use: "For thrips, spinosyns." },
      { name: "Neonicotinoids", type: "Chemical", use: "For insecticide resistance management." },
      { name: "Propiconazole", type: "Chemical", use: "For fungal diseases." }
    ],
    soil: "Deep, friable loam or sandy loam that is well-drained, fertile, and rich in organic matter with pH 6.0-7.5.",
    price: "Approx. ₹9.75-₹11.9 per kilogram."
  },
  broccoli: {
    pesticides: [
      { name: "Pyrethrin-based Spray", type: "organic", use: "to control a wide variety of insects, including mosquitoes, flies, cockroaches, and fleas." },
      { name: "Bacillus thuringiensis", type: "organic", use: "specifically targets caterpillars without harming beneficial insects." },
      { name: "iron phosphate slug bait", type: "organic", use: "to kill slugs without harming pets or wildlife." }
    ],
    soil: "loamy, well-draining soil rich in organic matter, with a slightly acidic pH between 6.0 and 7.0.",
    price: "Approx. ₹20-₹40 per kilogram."
      },
    capcicum: {
    pesticides: [
      { name: "neem oil", type: "organic", use: "Aphids, leafhoppers, psyllids, whiteflies, scale insects, and other homopterous pests." },
      { name: "Chlorantraniliprole", type: "organic", use: "to control lepidopteran pests like fruit borers, which cause damage to the fruits."}
    ],
    soil: "Well drained loamy soil rich in organic matter with pH 6.0-7.5.",
    price: "Approx. ₹60-₹80 per kilogram."
  }
};

function showInfo() {
  const plant = document.getElementById('plant-select').value;
  const infoDiv = document.getElementById('plant-info');
  const pesticideDiv = document.getElementById('pesticide-content');
  const soilDiv = document.getElementById('soil-content');
  const priceDiv = document.getElementById('price-content');
  
  if (!plant) {
    alert('Please select a plant.');
    return;
  }
  const data = plantData[plant];
  
  let pestHtml = '<ul>';
  data.pesticides.forEach(p => {
    pestHtml += `<li><strong>${p.name}</strong> (${p.type}): ${p.use}</li>`;
  });
  pestHtml += '</ul>';
  
  pesticideDiv.innerHTML = pestHtml;
  soilDiv.innerHTML = `<p>${data.soil}</p>`;
  priceDiv.innerHTML = `<p>${data.price}</p>`;
  infoDiv.style.display = 'block';
}
</script>
</body>
</html>
