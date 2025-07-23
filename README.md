<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>AI Web Dev Masterclass</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <style>
    .modal { display: none; }
    .modal.active { display: flex; }
  </style>
</head>

<body class="bg-gray-100 text-gray-800">
  <div class="min-h-screen flex items-center justify-center">
    <div class="bg-white shadow-lg rounded-lg p-8 max-w-lg text-center">
      <h1 class="text-3xl font-bold text-purple-700 mb-4">AI Web Dev Masterclass</h1>
      <p class="text-gray-600 mb-6">
        Learn to build websites using AI tools like ChatGPT, GitHub Copilot, and more.
      </p>
      <button id="payButton" class="bg-purple-600 hover:bg-purple-700 text-white px-6 py-3 rounded-lg font-semibold">
        Buy for Ksh 300
      </button>
    </div>
  </div>

  <!-- Modal -->
  <div id="mpesaModal" class="modal fixed inset-0 bg-black bg-opacity-50 items-center justify-center z-50">
    <div class="bg-white p-6 rounded-lg shadow-md w-full max-w-md relative">
      <h2 class="text-xl font-bold text-purple-700 mb-4">Complete Payment</h2>
      <p class="mb-2 text-sm text-gray-600">Enter your Safaricom number to receive the STK push.</p>
      <input type="text" id="phoneNumber" placeholder="07XXXXXXXX"
        class="w-full border border-gray-300 rounded px-4 py-2 mb-4 focus:outline-none focus:border-purple-500">
      <input type="email" id="buyerEmail" placeholder="Your email (optional)"
        class="w-full border border-gray-300 rounded px-4 py-2 mb-4 focus:outline-none focus:border-purple-500">
      <button id="payNowBtn" class="bg-green-600 hover:bg-green-700 text-white px-4 py-2 rounded w-full">
        Pay Now
      </button>
      <p id="mpesaMessage" class="text-sm text-center mt-4"></p>
      <button id="closeModal" class="absolute top-2 right-3 text-gray-500 hover:text-gray-800">&times;</button>
    </div>
  </div>

  <script>
    const payButton = document.getElementById("payButton");
    const mpesaModal = document.getElementById("mpesaModal");
    const closeModal = document.getElementById("closeModal");
    const payNowBtn = document.getElementById("payNowBtn");
    const phoneInput = document.getElementById("phoneNumber");
    const emailInput = document.getElementById("buyerEmail");
    const mpesaMessage = document.getElementById("mpesaMessage");

    payButton.addEventListener("click", () => mpesaModal.classList.add("active"));
    closeModal.addEventListener("click", () => {
      mpesaModal.classList.remove("active");
      mpesaMessage.textContent = "";
      phoneInput.value = "";
      emailInput.value = "";
    });

    function formatPhoneNumber(phone) {
      phone = phone.replace(/\s+/g, ''); // remove spaces
      if (phone.startsWith("07") && phone.length === 10) return "254" + phone.slice(1);
      if (phone.startsWith("254") && phone.length === 12) return phone;
      return "";
    }

    function displayMessage(message, type = "info") {
      mpesaMessage.textContent = message;
      mpesaMessage.className = `text-sm text-center mt-4 text-${type === "success" ? "green" : "red"}-600`;
      mpesaMessage.scrollIntoView({ behavior: 'smooth', block: 'center' });
    }

    payNowBtn.addEventListener('click', async function (e) {
      e.preventDefault();
      const phone = formatPhoneNumber(phoneInput.value.trim());
      const buyerEmail = emailInput.value.trim();

      if (!phone) {
        displayMessage("Enter a valid Safaricom number e.g. 07XXXXXXXX", "error");
        return;
      }

      payNowBtn.disabled = true;
      displayMessage("Sending STK push... Please wait.", "info");

      try {
        const response = await fetch("https://script.google.com/macros/s/AKfycbzspFKGb236uK719ULkvro5GRS7kAKwZuFDl0fOWNU60qge6oJEzDwku-03v04Ih5PP/exec", {
          method: "POST",
          headers: {
            "Content-Type": "application/json"
          },
          body: JSON.stringify({
            phone: phone,
            amount: 300,
            product: "AI Web Dev Masterclass",
            notify: "wanjalabrighton56@gmail.com",
            sendReceipt: true,
            buyerEmail: buyerEmail || `${phone}@safaricom.com`,
            sendBuyerReceipt: true
          })
        });

        const result = await response.json();

        if (result.success) {
          displayMessage(result.message || "STK Push sent successfully! Check your phone.", "success");
        } else {
          displayMessage(result.message || "Payment initiation failed. Please try again.", "error");
        }

      } catch (err) {
        displayMessage("Something went wrong. Please try again later.", "error");
        console.error("MPESA Error:", err);
      } finally {
        payNowBtn.disabled = false;
      }
    });
  </script>
</body>
</html>
