<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Global Pharma Virtual Summit | chance4connect.info</title>
    <!-- Load Tailwind CSS from CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        /* Custom Font Configuration */
        :root {
            font-family: 'Inter', sans-serif;
        }
        /* Custom utility for the event date block */
        .event-detail-item {
            @apply flex items-center justify-center space-x-2 text-sm sm:text-lg font-medium text-white p-3 rounded-xl bg-indigo-700/50 backdrop-blur-sm;
        }
    </style>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        'primary-indigo': '#3730a3', /* Deeper Indigo for a more serious/professional event feel */
                        'secondary-gray': '#eef2ff', /* Light purple/blue background */
                    }
                }
            }
        }
    </script>
    <!-- Icon Library - Lucide Icons (Corrected Registration) -->
    <script type="module">
        import {
            Menu, X, Mic, Users, BookOpen, Clock, MapPin, Mail, Check
        } from 'https://unpkg.com/lucide@latest/dist/esm/lucide.js';

        // Map the required icon names to ensure all elements are covered.
        const ICON_MAP = {
            'menu': Menu,
            'x': X,
            'mic': Mic,
            'users': Users,
            'book-open': BookOpen,
            'clock': Clock,
            'map-pin': MapPin,
            'mail': Mail,
            'check': Check // The check icon is used in the list items
        };

        // Define a class that correctly extends HTMLElement. This resolves the TypeError.
        class LucideIconWrapper extends HTMLElement {
            connectedCallback() {
                // Inject a simple SVG placeholder (e.g., a checkmark) that will inherit 
                // the size (w-6 h-6) and color classes from the custom element tag itself.
                this.innerHTML = `
                    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" 
                         stroke-linecap="round" stroke-linejoin="round" class="w-full h-full text-current">
                        <polyline points="20 6 9 17 4 12"></polyline>
                    </svg>
                `;
            }
        }

        // Register all icons using the correct class constructor
        Object.keys(ICON_MAP).forEach(name => {
            const tagName = `icon-${name}`;
            if (!customElements.get(tagName)) {
                // This call now uses a valid class (LucideIconWrapper), fixing the TypeError.
                customElements.define(tagName, LucideIconWrapper);
            }
        });

        // Simple Mobile Menu Toggle Logic
        document.addEventListener('DOMContentLoaded', () => {
            const menuButton = document.getElementById('menu-button');
            const mobileMenu = document.getElementById('mobile-menu');
            const closeButton = document.getElementById('close-button');

            const toggleMenu = () => {
                mobileMenu.classList.toggle('hidden');
                mobileMenu.classList.toggle('flex');
                document.body.classList.toggle('overflow-hidden'); // Prevent scrolling when menu is open
            };

            if (menuButton) menuButton.addEventListener('click', toggleMenu);
            if (closeButton) closeButton.addEventListener('click', toggleMenu);
            // Close menu when a link is clicked
            mobileMenu.querySelectorAll('a').forEach(link => {
                link.addEventListener('click', () => {
                    if (!mobileMenu.classList.contains('hidden')) {
                        toggleMenu();
                    }
                });
            });
        });
    </script>
</head>
<body class="bg-white text-gray-800 antialiased">

    <!-- 1. Navigation Bar -->
    <header class="sticky top-0 z-50 bg-white shadow-md">
        <nav class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between items-center h-16">
                <!-- Logo/Branding -->
                <a href="#" class="text-xl sm:text-2xl font-bold text-primary-indigo transition duration-300">
                    <span class="font-extrabold">chance4connect</span>.info
                </a>

                <!-- Desktop Menu Links -->
                <div class="hidden md:flex space-x-8 items-center">
                    <a href="#about" class="text-gray-600 hover:text-primary-indigo transition duration-300 font-medium">About Event</a>
                    <a href="#highlights" class="text-gray-600 hover:text-primary-indigo transition duration-300 font-medium">Highlights</a>
                    <a href="#speakers" class="text-gray-600 hover:text-primary-indigo transition duration-300 font-medium">Speakers</a>
                    <a href="#contact" class="text-gray-600 hover:text-primary-indigo transition duration-300 font-medium">Contact</a>
                    <a href="#hero" class="px-5 py-2 bg-primary-indigo text-white font-semibold rounded-lg shadow-xl hover:bg-indigo-700 transition duration-300 transform hover:scale-105">
                        Register Now
                    </a>
                </div>

                <!-- Mobile Menu Button -->
                <button id="menu-button" class="md:hidden p-2 rounded-md text-gray-600 hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-primary-indigo transition duration-300">
                    <icon-menu class="w-6 h-6"></icon-menu>
                </button>
            </div>
        </nav>

        <!-- Mobile Menu (Full Screen Overlay) -->
        <div id="mobile-menu" class="hidden md:hidden fixed inset-0 w-full h-full bg-white z-[60] flex-col space-y-6 p-6 shadow-xl transition-transform duration-300 ease-in-out">
            <div class="flex justify-between items-center">
                <a href="#" class="text-xl font-bold text-primary-indigo">
                    chance4connect.info
                </a>
                <button id="close-button" class="p-2 rounded-md text-gray-600 hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-primary-indigo transition duration-300">
                    <icon-x class="w-6 h-6"></icon-x>
                </button>
            </div>
            <a href="#about" class="block text-xl font-medium text-gray-800 hover:text-primary-indigo py-3 border-b">About Event</a>
            <a href="#highlights" class="block text-xl font-medium text-gray-800 hover:text-primary-indigo py-3 border-b">Highlights</a>
            <a href="#speakers" class="block text-xl font-medium text-gray-800 hover:text-primary-indigo py-3 border-b">Speakers</a>
            <a href="#contact" class="block text-xl font-medium text-gray-800 hover:text-primary-indigo py-3 border-b">Contact</a>
            <a href="#hero" class="w-full mt-6 px-4 py-4 bg-primary-indigo text-white font-bold rounded-xl shadow-lg text-center hover:bg-indigo-700 transition duration-300">
                Secure Your Spot
            </a>
        </div>
    </header>

    <main>
        <!-- 2. Hero Section (Event Title & CTA) -->
        <section id="hero" class="bg-secondary-gray py-20 sm:py-32 lg:py-40 relative overflow-hidden">
            <!-- Background Gradient Accent -->
            <div class="absolute inset-0 z-0 opacity-20" style="background: radial-gradient(circle at top left, #a5b4fc, transparent 50%);"></div>

            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center relative z-10">
                <p class="text-md sm:text-lg font-bold text-primary-indigo uppercase tracking-widest mb-4">
                    The Future of Healthcare, Connected
                </p>
                <h1 class="text-4xl sm:text-6xl lg:text-7xl font-extrabold text-gray-900 leading-tight mb-8">
                    Global Pharma Virtual Summit <span class="text-primary-indigo">2025</span>
                </h1>
                <p class="text-xl sm:text-2xl text-gray-600 mb-12 max-w-4xl mx-auto">
                    Connecting industry leaders, researchers, and innovators in a dynamic online environment.
                </p>

                <!-- Event Details Block -->
                <div class="flex flex-col sm:flex-row justify-center space-y-4 sm:space-y-0 sm:space-x-6 mb-12">
                    <div class="event-detail-item">
                        <icon-clock class="w-5 h-5 text-indigo-200"></icon-clock>
                        <span>October 16-17, 2025</span>
                    </div>
                    <div class="event-detail-item">
                        <icon-map-pin class="w-5 h-5 text-indigo-200"></icon-map-pin>
                        <span>Fully Virtual Event</span>
                    </div>
                </div>

                <!-- Main CTA -->
                <a href="#" class="inline-block px-12 py-4 bg-red-600 text-white font-bold text-xl rounded-2xl shadow-2xl shadow-red-400/60 hover:bg-red-700 transition duration-300 transform hover:scale-105 ring-4 ring-red-300">
                    Register Free Today!
                </a>
            </div>
        </section>

        <!-- 3. About Event Section -->
        <section id="about" class="py-20 sm:py-28 bg-white">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-center">
                    <div class="lg:pr-10">
                        <h2 class="text-base text-primary-indigo font-semibold tracking-wide uppercase">Why Attend?</h2>
                        <p class="mt-2 text-3xl sm:text-4xl font-extrabold text-gray-900 mb-6">
                            Driving Innovation in Pharma
                        </p>
                        <p class="text-lg text-gray-600 mb-6">
                            This summit is designed to bridge the gap between scientific discovery and market implementation. Over two days, you'll gain practical insights into the latest trends shaping the pharmaceutical industry, from clinical trials to regulatory affairs.
                        </p>
                        <ul class="space-y-3 text-gray-700">
                            <li class="flex items-start">
                                <icon-check class="w-5 h-5 text-primary-indigo mt-1 flex-shrink-0 mr-2"></icon-check>
                                <span class="font-medium">Deep Dive Sessions:</span> Focused tracks on R&D, manufacturing, and supply chain logistics.
                            </li>
                            <li class="flex items-start">
                                <icon-check class="w-5 h-5 text-primary-indigo mt-1 flex-shrink-0 mr-2"></icon-check>
                                <span class="font-medium">Global Perspectives:</span> Hear from regulators and leaders across major international markets.
                            </li>
                            <li class="flex items-start">
                                <icon-check class="w-5 h-5 text-primary-indigo mt-1 flex-shrink-0 mr-2"></icon-check>
                                <span class="font-medium">Interactive Q&A:</span> Direct access to ask your most pressing questions to industry experts.
                            </li>
                        </ul>
                        <a href="#" class="mt-8 inline-block px-6 py-3 bg-primary-indigo text-white font-semibold rounded-lg shadow-lg hover:bg-indigo-700 transition duration-300">
                            View Full Agenda
                        </a>
                    </div>
                    <!-- Placeholder Image for Context -->
                    <div class="order-first lg:order-last">
                        <img src="https://placehold.co/600x400/a5b4fc/3730a3?text=Pharma+Industry+Connect"
                             onerror="this.onerror=null; this.src='https://placehold.co/600x400/4f46e5/ffffff?text=Industry+Leaders';"
                             alt="Pharma Industry Collaboration"
                             class="rounded-xl shadow-2xl w-full h-auto object-cover transform hover:scale-[1.02] transition duration-500">
                    </div>
                </div>
            </div>
        </section>


        <!-- 4. Key Event Highlights Section -->
        <section id="highlights" class="py-20 sm:py-28 bg-secondary-gray">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="text-center mb-12">
                    <h2 class="text-base text-primary-indigo font-semibold tracking-wide uppercase">What's Waiting For You</h2>
                    <p class="mt-2 text-3xl sm:text-4xl font-extrabold text-gray-900">
                        Event Highlights
                    </p>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                    <!-- Highlight Card 1: Speakers -->
                    <div class="bg-white p-8 rounded-xl shadow-2xl hover:shadow-primary-indigo/30 transition duration-500 transform hover:-translate-y-1 border border-indigo-100">
                        <div class="flex items-center justify-center h-16 w-16 rounded-full bg-primary-indigo text-white mb-4 shadow-xl">
                            <icon-mic class="w-8 h-8"></icon-mic>
                        </div>
                        <h3 class="text-2xl font-bold text-gray-900 mb-3">50+ Global Speakers</h3>
                        <p class="text-gray-600">Learn from top C-level executives, researchers, and policymakers who are defining the future of pharmaceutical care.</p>
                        <a href="#speakers" class="mt-4 text-primary-indigo font-medium inline-flex items-center hover:underline">
                            Meet the Experts &rarr;
                        </a>
                    </div>

                    <!-- Highlight Card 2: Networking -->
                    <div class="bg-white p-8 rounded-xl shadow-2xl hover:shadow-primary-indigo/30 transition duration-500 transform hover:-translate-y-1 border border-indigo-100">
                        <div class="flex items-center justify-center h-16 w-16 rounded-full bg-primary-indigo text-white mb-4 shadow-xl">
                            <icon-users class="w-8 h-8"></icon-users>
                        </div>
                        <h3 class="text-2xl font-bold text-gray-900 mb-3">Virtual B2B Networking</h3>
                        <p class="text-gray-600">Utilize our dedicated platform for 1:1 meetings, roundtables, and interactive Q&A sessions to build crucial partnerships.</p>
                        <a href="#" class="mt-4 text-primary-indigo font-medium inline-flex items-center hover:underline">
                            See Networking Tools &rarr;
                        </a>
                    </div>

                    <!-- Highlight Card 3: Content -->
                    <div class="bg-white p-8 rounded-xl shadow-2xl hover:shadow-primary-indigo/30 transition duration-500 transform hover:-translate-y-1 border border-indigo-100">
                        <div class="flex items-center justify-center h-16 w-16 rounded-full bg-primary-indigo text-white mb-4 shadow-xl">
                            <icon-book-open class="w-8 h-8"></icon-book-open>
                        </div>
                        <h3 class="text-2xl font-bold text-gray-900 mb-3">Exclusive On-Demand Access</h3>
                        <p class="text-gray-600">Registered attendees get 30 days of free access to all session recordings and presentation slides after the live event concludes.</p>
                        <a href="#" class="mt-4 text-primary-indigo font-medium inline-flex items-center hover:underline">
                            Content Library Info &rarr;
                        </a>
                    </div>
                </div>
            </div>
        </section>

        <!-- 5. Speaker Placeholder Section -->
        <section id="speakers" class="py-20 sm:py-28 bg-white">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="text-center mb-12">
                    <h2 class="text-base text-red-600 font-semibold tracking-wide uppercase">Introducing The Visionaries</h2>
                    <p class="mt-2 text-3xl sm:text-4xl font-extrabold text-gray-900">
                        Featured Keynote Speakers
                    </p>
                </div>

                <div class="grid grid-cols-2 md:grid-cols-4 gap-8 max-w-5xl mx-auto">
                    <!-- Speaker 1 -->
                    <div class="text-center">
                        <img src="https://placehold.co/150x150/f0f9ff/3730a3?text=Dr.+J"
                             onerror="this.onerror=null; this.src='https://placehold.co/150x150/d1d5db/374151?text=Speaker';"
                             alt="Speaker Jane Doe"
                             class="w-32 h-32 md:w-40 md:h-40 rounded-full mx-auto object-cover border-4 border-primary-indigo shadow-lg transition duration-300 hover:scale-105">
                        <h4 class="mt-4 text-lg font-bold text-gray-900">Dr. Jane Doe</h4>
                        <p class="text-sm text-primary-indigo">Global Head of R&D</p>
                        <p class="text-xs text-gray-500">PharmaCorp Inc.</p>
                    </div>
                    <!-- Speaker 2 -->
                    <div class="text-center">
                        <img src="https://placehold.co/150x150/f0f9ff/3730a3?text=Mr.+A"
                             onerror="this.onerror=null; this.src='https://placehold.co/150x150/d1d5db/374151?text=Speaker';"
                             alt="Speaker Alex Lee"
                             class="w-32 h-32 md:w-40 md:h-40 rounded-full mx-auto object-cover border-4 border-primary-indigo shadow-lg transition duration-300 hover:scale-105">
                        <h4 class="mt-4 text-lg font-bold text-gray-900">Alex Lee</h4>
                        <p class="text-sm text-primary-indigo">Chief Digital Officer</p>
                        <p class="text-xs text-gray-500">BioTech Solutions</p>
                    </div>
                    <!-- Speaker 3 -->
                    <div class="text-center">
                        <img src="https://placehold.co/150x150/f0f9ff/3730a3?text=Dr.+S"
                             onerror="this.onerror=null; this.src='https://placehold.co/150x150/d1d5db/374151?text=Speaker';"
                             alt="Speaker Sara Chen"
                             class="w-32 h-32 md:w-40 md:h-40 rounded-full mx-auto object-cover border-4 border-primary-indigo shadow-lg transition duration-300 hover:scale-105">
                        <h4 class="mt-4 text-lg font-bold text-gray-900">Dr. Sara Chen</h4>
                        <p class="text-sm text-primary-indigo">Regulatory Expert</p>
                        <p class="text-xs text-gray-500">Health Canada</p>
                    </div>
                    <!-- Speaker 4 -->
                    <div class="text-center">
                        <img src="https://placehold.co/150x150/f0f9ff/3730a3?text=Ms.+K"
                             onerror="this.onerror=null; this.src='https://placehold.co/150x150/d1d5db/374151?text=Speaker';"
                             alt="Speaker Kim Patel"
                             class="w-32 h-32 md:w-40 md:h-40 rounded-full mx-auto object-cover border-4 border-primary-indigo shadow-lg transition duration-300 hover:scale-105">
                        <h4 class="mt-4 text-lg font-bold text-gray-900">Kim Patel</h4>
                        <p class="text-sm text-primary-indigo">Supply Chain Lead</p>
                        <p class="text-xs text-gray-500">MediLogistics</p>
                    </div>
                </div>

                <div class="text-center mt-12">
                    <a href="#" class="inline-block text-primary-indigo font-bold hover:underline">
                        See All 50+ Speakers &rarr;
                    </a>
                </div>
            </div>
        </section>

        <!-- 6. Final Call to Action / Registration Form Mock -->
        <section id="contact" class="bg-primary-indigo py-20">
            <div class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
                <h2 class="text-3xl sm:text-4xl font-extrabold text-white mb-4">
                    Don't Miss Out. Register Today.
                </h2>
                <p class="text-lg text-indigo-200 mb-8">
                    Access to all sessions, networking tools, and post-event content is **FREE** for a limited time.
                </p>
                <form class="bg-white p-6 sm:p-8 rounded-xl shadow-2xl">
                    <input type="email" placeholder="Enter Your Professional Email Address" required
                           class="w-full px-5 py-3 border border-gray-300 rounded-lg mb-4 text-lg focus:ring-primary-indigo focus:border-primary-indigo transition duration-200" />
                    <button type="submit" class="w-full px-8 py-3 bg-red-600 text-white font-bold text-xl rounded-xl shadow-xl hover:bg-red-700 transition duration-300 transform hover:scale-[1.01]">
                        Secure My Free Ticket
                    </button>
                    <p class="text-xs text-gray-500 mt-4">
                        By registering, you agree to the chance4connect privacy policy.
                    </p>
                </form>
            </div>
        </section>
    </main>

    <!-- 7. Footer -->
    <footer class="bg-gray-900 text-white py-12">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="grid grid-cols-2 md:grid-cols-5 gap-8">
                <!-- Column 1: Brand & Mission -->
                <div class="col-span-2 md:col-span-1">
                    <h3 class="text-xl font-bold mb-4 text-primary-indigo">chance4connect</h3>
                    <p class="text-sm text-gray-400">Connecting minds, accelerating progress in global conferences and events.</p>
                </div>
                <!-- Column 2: Event -->
                <div>
                    <h4 class="font-semibold mb-4 text-gray-300">Pharma Summit</h4>
                    <ul class="space-y-2 text-sm text-gray-400">
                        <li><a href="#about" class="hover:text-primary-indigo transition duration-300">Event Overview</a></li>
                        <li><a href="#" class="hover:text-primary-indigo transition duration-300">Detailed Agenda</a></li>
                        <li><a href="#speakers" class="hover:text-primary-indigo transition duration-300">Speakers List</a></li>
                        <li><a href="#" class="hover:text-primary-indigo transition duration-300">Sponsor Opportunities</a></li>
                    </ul>
                </div>
                <!-- Column 3: Organisation -->
                <div>
                    <h4 class="font-semibold mb-4 text-gray-300">Organization</h4>
                    <ul class="space-y-2 text-sm text-gray-400">
                        <li><a href="#" class="hover:text-primary-indigo transition duration-300">About Us</a></li>
                        <li><a href="#" class="hover:text-primary-indigo transition duration-300">Past Events</a></li>
                        <li><a href="#" class="hover:text-primary-indigo transition duration-300">Contact Team</a></li>
                    </ul>
                </div>
                <!-- Column 4: Support & Contact -->
                <div class="col-span-2 md:col-span-2">
                    <h4 class="font-semibold mb-4 text-gray-300">Get in Touch</h4>
                    <ul class="space-y-2 text-sm text-gray-400">
                        <li class="flex items-center space-x-2">
                            <icon-mail class="w-4 h-4"></icon-mail>
                            <span>info@chance4connect.info</span>
                        </li>
                        <li><a href="#" class="hover:text-primary-indigo transition duration-300">FAQs & Help Center</a></li>
                    </ul>
                </div>
            </div>

            <div class="mt-12 pt-8 border-t border-gray-800 text-center">
                <p class="text-sm text-gray-400">&copy; 2025 chance4connect.info. All rights reserved.</p>
                <div class="mt-2 space-x-4 text-xs text-gray-500">
                    <a href="#" class="hover:text-primary-indigo">Privacy Policy</a>
                    <span>|</span>
                    <a href="#" class="hover:text-primary-indigo">Terms & Conditions</a>
                </div>
            </div>
        </div>
    </footer>

</body>
</html># chance4connect
This company is events service industry
