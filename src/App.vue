<template>
  <div id="app">
    <!-- Wrapper -->
    <div id="wrapper" class="fade-in">
      <!-- Intro -->
      <div id="intro">
        <h1>Stream-It</h1>
        <p>
          Don't know what to watch tonight? Enter some details about the kind of movie you're looking for and we'll make
          the perfect suggestion for you!
        </p>
        <ul class="actions">
          <li><a href="#header" class="button icon solid solo fa-arrow-down scrolly">Continue</a></li>
        </ul>
      </div>

      <!-- Header -->
      <header id="header">
        <!-- <a href="/" class="home">Website powered by Watchmode</a> -->
      </header>
      <router-view />

      <!-- Footer -->
      <footer id="footer">
        <section>
          <form method="post" action="#">
            <div class="fields">
              <div class="field">
                <label for="name">Name</label>
                <input type="text" name="name" id="name" />
              </div>
              <div class="field">
                <label for="email">Email</label>
                <input type="text" name="email" id="email" />
              </div>
              <div class="field">
                <label for="message">Message</label>
                <textarea name="message" id="message" rows="3"></textarea>
              </div>
            </div>
            <ul class="actions">
              <li><input type="submit" value="Send Message" /></li>
            </ul>
          </form>
        </section>
        <section class="split contact">
          <section class="alt">
            <h3>Address</h3>
            <p>
              1234 Somewhere Road #87257
              <br />
              Nashville, TN 00000-0000
            </p>
          </section>
          <section>
            <h3>Phone</h3>
            <p><a href="#">(000) 000-0000</a></p>
          </section>
          <section>
            <h3>Email</h3>
            <p><a href="#">info@untitled.tld</a></p>
          </section>
          <section>
            <h3>Social</h3>
            <ul class="icons alt">
              <li>
                <a href="#" class="icon brands alt fa-twitter"><span class="label">Twitter</span></a>
              </li>
              <li>
                <a href="#" class="icon brands alt fa-facebook-f"><span class="label">Facebook</span></a>
              </li>
              <li>
                <a href="#" class="icon brands alt fa-instagram"><span class="label">Instagram</span></a>
              </li>
              <li>
                <a href="#" class="icon brands alt fa-github"><span class="label">GitHub</span></a>
              </li>
            </ul>
          </section>
        </section>
      </footer>

      <!-- Copyright -->
      <div id="copyright">
        <ul>
          <li>&copy; Stream-It 2021</li>
          <li>
            Design:
            <a href="https://gcarter24.github.io/">George Chris Carter</a>
            <a href="https://html5up.net">& HTML5 UP</a>
            <br />
          </li>
        </ul>
        <a href="https://api.watchmode.com/" class="home">Website powered by Watchmode API</a>
      </div>
    </div>

    |
    <router-link to="/about">About</router-link>
    |
    <router-link to="/movies/:id">Movies</router-link>
    |
    <router-link to="/movies/random">Random</router-link>
  </div>
</template>

<style></style>
