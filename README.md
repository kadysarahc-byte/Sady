<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Sady Stitch - Boutique Mobile</title>
<style>
  body { font-family: Arial, sans-serif; margin:0; padding:0; background:#fff;}
  header { background:#f8c8d8; padding:20px; text-align:center; color:#333; }
  header h1 { margin:0; font-size:2em; }
  header p { margin:5px 0; }
  
  /* CARROUSEL */
  .carousel { display:flex; overflow-x:auto; scroll-snap-type:x mandatory; padding:20px 0; }
  .carousel::-webkit-scrollbar { display:none; }
  .carousel-item { flex:0 0 auto; scroll-snap-align:start; margin:0 10px; border:1px solid #ddd; border-radius:10px; padding:10px; width:200px; text-align:center; background:#fff; }
  .carousel-item img { width:100%; border-radius:10px; }
  .carousel-item h3 { margin:10px 0 5px; }
  .carousel-item p { margin:5px 0; font-weight:bold; }

  .form-section { background:#fce4ec; padding:20px; margin:20px auto; width:90%; max-width:500px; border-radius:10px; }
  .form-section h2 { text-align:center; }
  input, select, textarea, button { width:100%; padding:10px; margin:10px 0; border-radius:5px; border:1px solid #ccc; }
  button { background:#f06292; color:white; border:none; cursor:pointer; }
  button:hover { background:#e91e63; }
  .contact { text-align:center; margin:20px; }
  footer { background:#f8c8d8; padding:10px; text-align:center; }

</style>
</head>
<body>

<header>
  <h1>Sady Stitch</h1>
  <p>Élégance et qualité pour vos accessoires</p>
  <p>Contact WhatsApp : <a href="https://wa.me/2250101361622" target="_blank">+225 0101361622</a></p>
</header>

<!-- CARROUSEL PRODUITS -->
<section class="carousel">
  <div class="carousel-item">
    <img src="bonnet1000.jpg" alt="Bonnet 1000f">
    <h3>Bonnet</h3>
    <p>1000 F</p>
  </div>
  <div class="carousel-item">
    <img src="bonnet1500.jpg" alt="Bonnet 1500f">
    <h3>Bonnet</h3>
    <p>1500 F</p>
  </div>
  <div class="carousel-item">
    <img src="bonnet2000.jpg" alt="Bonnet 2000f">
    <h3>Bonnet</h3>
    <p>2000 F</p>
  </div>
  <div class="carousel-item">
    <img src="chouchou300.jpg" alt="Chouchou 300f">
    <h3>Chouchou</h3>
    <p>300 F</p>
  </div>
  <div class="carousel-item">
    <img src="chouchou500.jpg" alt="Chouchou 2 pour 500f">
    <h3>Chouchou</h3>
    <p>2 pour 500 F</p>
  </div>
  <div class="carousel-item">
    <img src="noeud500.jpg" alt="Noeud 500f">
    <h3>Noeud</h3>
    <p>500 F</p>
  </div>
</section>

<!-- FORMULAIRE COMMANDE & PAIEMENT -->
<section class="form-section">
  <h2>Commande & Paiement Wave</h2>
  <form id="orderForm">
    <input type="text" id="name" placeholder="Nom complet" required>
    <input type="tel" id="phone" placeholder="Numéro de téléphone" required>
    
    <select id="product" required>
      <option value="">Choisir un produit</option>
      <option value="1000">Bonnet 1000 F</option>
      <option value="1500">Bonnet 1500 F</option>
      <option value="2000">Bonnet 2000 F</option>
      <option value="300">Chouchou 300 F</option>
      <option value="500">Chouchou 2 pour 500 F</option>
      <option value="500n">Noeud 500 F</option>
    </select>
    
    <input type="number" id="quantity" placeholder="Quantité" min="1" value="1" required>
    <textarea id="comments" placeholder="Commentaire ou demande spéciale"></textarea>
    
    <p>Total : <span id="total">0</span> F</p>
    
    <button type="button" onclick="payWithWave()">Payer avec Wave</button>
  </form>
</section>

<div class="contact">
  <p>Vos informations sont sécurisées 🔒</p>
  <p>Pour toute question, contactez-nous sur WhatsApp : <a href="https://wa.me/2250101361622" target="_blank">+225 0101361622</a></p>
</div>

<footer>
  &copy; 2025 Sady Stitch. Tous droits réservés.
</footer>

<script>
  const productSelect = document.getElementById('product');
  const quantityInput = document.getElementById('quantity');
  const totalSpan = document.getElementById('total');

  function updateTotal() {
    const price = parseInt(productSelect.value) || 0;
    const qty = parseInt(quantityInput.value) || 1;
    totalSpan.textContent = price * qty;
  }

  productSelect.addEventListener('change', updateTotal);
  quantityInput.addEventListener('input', updateTotal);

  function payWithWave() {
    const name = document.getElementById('name').value;
    const phone = document.getElementById('phone').value;
    const product = productSelect.options[productSelect.selectedIndex].text;
    const qty = quantityInput.value;
    const total = totalSpan.textContent;

    if (!name || !phone || !productSelect.value) {
      alert("Veuillez remplir tous les champs !");
      return;
    }

    // Ici tu peux utiliser l'API Wave pour créer un paiement direct
    // Pour l'exemple, on simule un paiement intégré
    alert(`Commande : ${product} x${qty}\nTotal : ${total} F\nVous serez redirigé vers Wave pour le paiement.`);

    // Exemple de redirection vers Wave
    const paymentUrl = `https://wave.com/paiement?amount=${total}&name=${encodeURIComponent(name)}&phone=${encodeURIComponent(phone)}`;
    window.open(paymentUrl, "_blank");
  }

  updateTotal(); // Initial total
</script>

</body>
</html>
