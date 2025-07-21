<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI Web Dev Masterclass - Get Yours Now!</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <!-- Font Awesome for icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f3f4f6; /* Light gray background */
            color: #374151; /* Dark gray text */
        }
        .header-bg {
            background-color: #1a202c; /* Dark charcoal */
        }
        .product-section-bg {
            background: linear-gradient(135deg, #4f46e5, #6366f1, #818cf8); /* Indigo gradient */
            color: white;
        }
        .cta-button {
            background-color: #facc15; /* Gold */
            color: #1f2937; /* Dark text */
            transition: all 0.3s ease;
        }
        .cta-button:hover {
            background-color: #fbbf24; /* Lighter gold */
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
        }
        .modal-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.7);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 10000;
            opacity: 0;
            visibility: hidden;
            transition: opacity 0.3s ease;
        }
        .modal-overlay.show {
            opacity: 1;
            visibility: visible;
        }
        .modal-content {
            background: white;
            border-radius: 12px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            width: 90%;
            max-width: 450px;
            padding: 24px;
            position: relative;
            transform: translateY(-20px);
            transition: transform 0.3s ease;
            display: flex;
            flex-direction: column;
            align-items: center;
            text-align: center;
            color: #374151;
        }
        .modal-overlay.show .modal-content {
            transform: translateY(0);
        }
        .modal-close-btn {
            position: absolute;
            top: 12px;
            right: 12px;
            background: none;
            border: none;
            font-size: 1.5rem;
            color: #6b7280;
            cursor: pointer;
            transition: color 0.2s, transform 0.2s;
        }
        .modal-close-btn:hover {
            color: #1f2937;
            transform: scale(1.2);
        }
        .input-field {
            border: 1px solid #d1d5db;
            padding: 10px 14px;
            border-radius: 8px;
            width: 100%;
            margin-bottom: 16px;
            font-size: 1rem;
            color: #374151;
            background-color: #f9fafb;
        }
        .input-field:focus {
            outline: none;
            border-color: #4f46e5;
            box-shadow: 0 0 0 3px rgba(79, 70, 229, 0.2);
        }
        .pay-button {
            background-color: #059669; /* M-Pesa Green */
            color: white;
            padding: 12px 24px;
            border-radius: 8px;
            font-weight: bold;
            cursor: pointer;
            transition: background-color 0.2s, transform 0.2s, box-shadow 0.2s;
            width: 100%;
            border: none;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
        }
        .pay-button:hover {
            background-color: #047857; /* Darker M-Pesa Green */
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
        }
        .pay-button:disabled {
            background-color: #a7f3d0; /* Light green for disabled */
            cursor: not-allowed;
            transform: none;
            box-shadow: none;
        }
        .loading-spinner {
            border: 4px solid rgba(255, 255, 255, 0.3);
            border-top-color: #fff;
            border-radius: 50%;
            width: 24px;
            height: 24px;
            animation: spin 1s linear infinite;
        }
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        .message-box {
            padding: 12px;
            border-radius: 8px;
            margin-top: 16px;
            font-weight: 500;
            display: none; /* Hidden by default */
            text-align: left;
            width: 100%;
        }
        .message-box.success {
            background-color: #d1fae5; /* Green-100 */
            color: #065f46; /* Green-900 */
            border: 1px solid #34d399; /* Green-400 */
        }
        .message-box.error {
            background-color: #fee2e2; /* Red-100 */
            color: #991b1b; /* Red-900 */
            border: 1px solid #f87171; /* Red-400 */
        }
        .message-box.info {
            background-color: #e0f2fe; /* Blue-100 */
            color: #1e40af; /* Blue-900 */
            border: 1px solid #60a5fa; /* Blue-400 */
        }
    </style>
</head>
<body class="text-gray-800">

    <!-- Header -->
    <header class="header-bg text-white py-4 shadow-md">
        <div class="container mx-auto px-6 flex justify-between items-center">
            <div class="flex items-center space-x-2">
                <div class="relative w-10 h-10 bg-indigo-500 rounded-full flex items-center justify-center text-white font-bold text-lg">
                    <span>AI</span>
                </div>
                <h1 class="text-2xl font-bold">AI Dev Masterclass</h1>
            </div>
            <nav>
                <a href="#" class="text-gray-300 hover:text-white font-medium">Home</a>
                <!-- Add more navigation links if needed -->
            </nav>
        </div>
    </header>

    <main>
        <!-- Product Section -->
        <section class="product-section-bg py-20">
            <div class="container mx-auto px-6 flex flex-col md:flex-row items-center justify-center gap-12">
                <!-- Product Image -->
                <div class="md:w-1/2 flex justify-center">
                    <img src="https://placehold.co/600x400/6366f1/FFFFFF?text=AI+Web+Dev+Masterclass" alt="AI Web Dev Masterclass Product" class="rounded-xl shadow-2xl max-w-full h-auto object-cover">
                </div>
                <!-- Product Details -->
                <div class="md:w-1/2 text-center md:text-left">
                    <h2 class="text-5xl font-bold mb-4">AI Web Dev Masterclass</h2>
                    <p class="text-xl mb-6 leading-relaxed max-w-xl mx-auto md:mx-0">Unlock the secrets of AI-powered web development with this comprehensive masterclass. Learn to build professional, dynamic, and scalable websites with cutting-edge tools and techniques. Perfect for aspiring AI developers and designers.</p>
                    <p class="text-4xl font-extrabold mb-8 text-yellow-300">KES 1,200</p>
                    <button id="buy-now-btn" class="cta-button py-3 px-10 rounded-lg text-xl font-bold shadow-lg hover:shadow-xl">
                        <i class="fas fa-shopping-cart mr-3"></i> Buy Now
                    </button>
                </div>
            </div>
        </section>

        <!-- Features/Benefits Section (Optional, but good for a product page) -->
        <section class="py-16 bg-white">
            <div class="container mx-auto px-6 text-center">
                <h3 class="text-3xl font-bold text-gray-800 mb-10">What You'll Learn</h3>
                <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
                    <div class="p-6 bg-gray-50 rounded-lg shadow-md flex flex-col items-center">
                        <div class="text-indigo-600 text-4xl mb-4"><i class="fas fa-brain"></i></div>
                        <h4 class="text-xl font-semibold mb-2">AI-Driven Design</h4>
                        <p class="text-gray-600">Master prompts and techniques to guide AI in creating stunning, responsive web designs.</p>
                    </div>
                    <div class="p-6 bg-gray-50 rounded-lg shadow-md flex flex-col items-center">
                        <div class="text-indigo-600 text-4xl mb-4"><i class="fas fa-code"></i></div>
                        <h4 class="text-xl font-semibold mb-2">Efficient Code Generation</h4>
                        <p class="text-gray-600">Learn to leverage AI for rapid, clean, and maintainable code across various frameworks.</p>
                    </div>
                    <div class="p-6 bg-gray-50 rounded-lg shadow-md flex flex-col items-center">
                        <div class="text-indigo-600 text-4xl mb-4"><i class="fas fa-database"></i></div>
                        <h4 class="text-xl font-semibold mb-2">Backend Integration</h4>
                        <p class="text-gray-600">Understand how to connect your AI-generated frontends with powerful backend services like Firebase.</p>
                    </div>
                    <div class="p-6 bg-gray-50 rounded-lg shadow-md flex flex-col items-center">
                        <div class="text-indigo-600 text-4xl mb-4"><i class="fas fa-bug"></i></div>
                        <h4 class="text-xl font-semibold mb-2">Advanced Debugging</h4>
                        <p class="text-gray-600">Develop strategies to diagnose and resolve complex errors, including API and CORS issues.</p>
                    </div>
                    <div class="p-6 bg-gray-50 rounded-lg shadow-md flex flex-col items-center">
                        <div class="text-indigo-600 text-4xl mb-4"><i class="fas fa-mobile-alt"></i></div>
                        <h4 class="text-xl font-semibold mb-2">Responsive Development</h4>
                        <p class="text-gray-600">Build websites that look and perform flawlessly on any device, from mobile to desktop.</p>
                    </div>
                    <div class="p-6 bg-gray-50 rounded-lg shadow-md flex flex-col items-center">
                        <div class="text-indigo-600 text-4xl mb-4"><i class="fas fa-rocket"></i></div>
                        <h4 class="text-xl font-semibold mb-2">Deployment & Beyond</h4>
                        <p class="text-gray-600">Get insights into deploying your AI-crafted web apps and scaling them for real-world use.</p>
                    </div>
                </div>
            </div>
        </section>
    </main>

    <!-- Footer -->
    <footer class="bg-gray-900 text-white py-8">
        <div class="container mx-auto px-6 text-center">
            <p>&copy; 2025 AI Dev Masterclass. All Rights Reserved.</p>
            <p class="text-sm text-gray-400 mt-2">Powered by cutting-edge AI development.</p>
        </div>
    </footer>

    <!-- M-Pesa Payment Modal -->
    <div id="mpesa-modal-overlay" class="modal-overlay">
        <div class="modal-content">
            <button id="mpesa-modal-close-btn" class="modal-close-btn">&times;</button>
            <h3 class="text-2xl font-bold mb-4">Complete Your Purchase</h3>
            <p class="text-gray-600 mb-6">Enter your M-Pesa phone number to receive the STK Push for KES <span id="product-price-display">1,200</span>.</p>
            
            <div class="w-full mb-4">
                <label for="phone-number" class="block text-left text-sm font-medium text-gray-700 mb-2">M-Pesa Phone Number (e.g., 07XXXXXXXX)</label>
                <input type="tel" id="phone-number" class="input-field" placeholder="07XXXXXXXX" pattern="^(07|2547)\d{8}$" required>
            </div>

            <button id="pay-now-btn" class="pay-button">
                <i class="fas fa-money-bill-wave mr-2"></i> Pay Now
            </button>

            <!-- Message Box for feedback -->
            <div id="mpesa-message" class="message-box"></div>
        </div>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function () {
            const buyNowBtn = document.getElementById('buy-now-btn');
            const mpesaModalOverlay = document.getElementById('mpesa-modal-overlay');
            const mpesaModalCloseBtn = document.getElementById('mpesa-modal-close-btn');
            const phoneNumberInput = document.getElementById('phone-number');
            const payNowBtn = document.getElementById('pay-now-btn');
            const mpesaMessage = document.getElementById('mpesa-message');
            const productPriceDisplay = document.getElementById('product-price-display');

            const PRODUCT_PRICE = 1200; // Define product price
            const PRODUCT_NAME = "AI Web Dev Masterclass"; // Define product name

            // Display product price in the modal
            productPriceDisplay.textContent = PRODUCT_PRICE.toLocaleString();

            // Function to show modal
            function showModal() {
                mpesaModalOverlay.classList.add('show');
                mpesaMessage.style.display = 'none'; // Hide message on modal open
                mpesaMessage.className = 'message-box'; // Reset message box classes
                payNowBtn.disabled = false; // Enable button
                payNowBtn.innerHTML = '<i class="fas fa-money-bill-wave mr-2"></i> Pay Now'; // Reset button text
                phoneNumberInput.value = ''; // Clear phone number field
            }

            // Function to hide modal
            function hideModal() {
                mpesaModalOverlay.classList.remove('show');
            }

            // Event listeners for modal
            buyNowBtn.addEventListener('click', showModal);
            mpesaModalCloseBtn.addEventListener('click', hideModal);
            mpesaModalOverlay.addEventListener('click', function(e) {
                if (e.target === mpesaModalOverlay) { // Only close if clicking on the overlay itself
                    hideModal();
                }
            });

            // Function to display messages in the message box
            function displayMessage(message, type) {
                mpesaMessage.textContent = message;
                mpesaMessage.className = `message-box ${type}`;
                mpesaMessage.style.display = 'block';
            }

            // M-Pesa Payment Logic
            payNowBtn.addEventListener('click', async function() {
                const phoneNumber = phoneNumberInput.value.trim();

                // Basic phone number validation (Kenya format: 07XXXXXXXX or 2547XXXXXXXX)
                const phoneRegex = /^(07|2547)\d{8}$/;
                if (!phoneRegex.test(phoneNumber)) {
                    displayMessage("Please enter a valid M-Pesa phone number (e.g., 07XXXXXXXX or 2547XXXXXXXX).", "error");
                    return;
                }

                // Format phone number to 254XXXXXXXXXXX
                let formattedPhoneNumber = phoneNumber;
                if (formattedPhoneNumber.startsWith('07')) {
                    formattedPhoneNumber = '254' + formattedPhoneNumber.substring(1);
                }

                payNowBtn.disabled = true;
                payNowBtn.innerHTML = '<div class="loading-spinner"></div> Initiating...';
                displayMessage("Initiating M-Pesa STK Push... Please wait.", "info");

                // IMPORTANT: This URL has been updated with the one you provided.
                const mpesaApiProxyUrl = 'https://script.google.com/macros/s/AKfycbzspFKGb236uK719ULkvro5GRS7kAKwZuFDl0fOWNU60qge6oJEzDwku-03v04Ih5PP/exec'; 
                
                try {
                    const response = await fetch(mpesaApiProxyUrl, {
                        method: 'POST',
                        headers: {
                            'Content-Type': 'application/json',
                        },
                        mode: 'cors',
                        body: JSON.stringify({
                            phoneNumber: formattedPhoneNumber,
                            amount: PRODUCT_PRICE,
                            productName: PRODUCT_NAME
                        }),
                    });

                    if (!response.ok) {
                        const errorText = await response.text();
                        console.error('M-Pesa Proxy Fetch Error (Response Not OK):', response.status, response.statusText, errorText);
                        displayMessage(`Payment initiation failed: ${response.statusText || 'Server Error'}. Please try again.`, "error");
                        payNowBtn.disabled = false;
                        payNowBtn.innerHTML = '<i class="fas fa-money-bill-wave mr-2"></i> Pay Now';
                        return;
                    }

                    const result = await response.json();
                    console.log('M-Pesa Proxy Response:', result);

                    if (result.success) {
                        displayMessage(result.message, "success");
                        // Optionally, you can hide the modal after a successful STK push initiation
                        // setTimeout(hideModal, 5000);
                    } else {
                        displayMessage(`Payment initiation failed: ${result.message}`, "error");
                    }

                } catch (error) {
                    console.error('Error initiating M-Pesa STK Push:', error);
                    displayMessage("Network error or failed to connect to payment service. Please check your internet and try again.", "error");
                } finally {
                    payNowBtn.disabled = false;
                    payNowBtn.innerHTML = '<i class="fas fa-money-bill-wave mr-2"></i> Pay Now';
                }
            });
        });
    </script>
</body>
</html>
