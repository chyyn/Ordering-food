<template>
    <section class="contact" id="contact">
        <div class="contact">
            <img :src="logo" id="footerlogo" alt="Home" width="100px" height="auto" loading="lazy">

            <div class="icons">
                <a href="" aria-label="facebook"><i class="bx bxl-facebook"></i></a>
                <a href="" aria-label="twitter"><i class="bx bxl-twitter"></i></a>
                <a href="" aria-label="instagram"><i class="bx bxl-instagram-alt"></i></a>
                <a href="" aria-label="youtube"><i class="bx bxl-youtube"></i></a>
            </div>
        </div>

        <div class="contact-box">
            <h3>Support</h3>
            <ul>
                <li><a href="#">Contact Us</a></li>
                <li><a href="#">FAQs</a></li>
                <li><a href="#">Terms of Service</a></li>
                <li><a href="#">Privacy Policy</a></li>
            </ul>
        </div>

        <div class="contact-box">
            <h3>Our menu</h3>
            <ul>
                <li><a href="#">Breakfast</a></li>
                <li><a href="#">Lunch</a></li>
                <li><a href="#">Dinner</a></li>
                <li><a href="#">Specials</a></li>
            </ul>
        </div>
    </section>

</template>

<script>
export default {
    name: 'ContactFooter',
    props: ['logo']
}
</script>