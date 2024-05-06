<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Webpage</title>
    <style>
        /* Basic styling (add your CSS here) */
        .hidden { display: none; }
    </style>
</head>
<body>
    <header>
        <h1>Interactive JavaScript Features</h1>
    </header>

    <!-- Navigation Menu -->
    <nav id="navMenu">
        <button onclick="toggleMenu()">Toggle Menu</button>
        <ul class="hidden">
            <li>Home</li>
            <li>About</li>
            <li>Services</li>
            <li>Contact</li>
        </ul>
    </nav>

    <!-- Form with Validation -->
    <form id="contactForm">
        <label for="email">Email:</label>
        <input type="email" id="email" required>
        <button type="submit">Submit</button>
    </form>

    <!-- Dynamic Content Section -->
    <div id="dynamicContent">
        <button onclick="updateContent()">Update Content</button>
        <p>Content will be updated here.</p>
    </div>

    <script>
        // Toggle Menu Visibility
        function toggleMenu() {
            const menu = document.querySelector('nav ul');
            menu.classList.toggle('hidden');
        }

        // Form Validation and XSS Protection
        document.getElementById('contactForm').addEventListener('submit', function(event) {
            event.preventDefault();
            const emailInput = document.getElementById('email');
            const email = emailInput.value;
            // Simple email validation
            if (!email.match(/^\w+([.-]?\w+)*@\w+([.-]?\w+)*(\.\w{2,3})+$/)) {
                alert("Please enter a valid email address.");
                return;
            }
            // Encode email to prevent XSS
            const safeEmail = encodeURIComponent(email);
            alert("Thank you, your email " + safeEmail + " has been submitted securely.");
        });

        // Dynamic Content Updates
        function updateContent() {
            const contentArea = document.getElementById('dynamicContent').querySelector('p');
            contentArea.textContent = "Updated with new information at " + new Date().toLocaleTimeString();
        }
    </script>
</body>
</html>
