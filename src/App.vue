<template>
  <div id="app">
    <!-- Wrapper -->
    <div id="wrapper" class="fade-in">
      <!-- Header -->
      <header id="header">
        <!-- <a href="/" class="home">Website powered by Watchmode</a> -->
      </header>
      <!-- Nav -->
      <nav id="nav">
        <ul class="links">
          <li class=""><a href="/">Homepage</a></li>
          <li><a href="/movies">Movies</a></li>
          <!-- <li><a href="/elements.html">Elements Reference</a></li> -->
        </ul>
        <ul class="icons">
          <!-- <li>
            <a href="#" class="icon brands fa-twitter"><span class="label">Twitter</span></a>
          </li>
          <li>
            <a href="#" class="icon brands fa-facebook-f"><span class="label">Facebook</span></a>
          </li> -->
          <li>
            <a href="https://www.linkedin.com/in/georgechriscarter/" class="icon brands alt fa-linkedin">
              <span class="label">LinkedIn</span>
            </a>
          </li>
          <li>
            <a href="https://github.com/gcarter24" class="icon brands fa-github"><span class="label">GitHub</span></a>
          </li>
        </ul>
      </nav>

      <router-view />

      <!-- Footer -->
      <!-- <footer id="footer">
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
      </footer> -->

      <!-- Copyright -->
      <div id="copyright">
        <ul>
          <li>&copy;2021 Stream-It</li>
          <li>
            Design:
            <a href="https://gcarter24.github.io/">George Chris Carter</a>
            <a>&</a>
            <a href="https://html5up.net">HTML5 UP</a>
            <br />
          </li>
        </ul>
        <a href="https://api.watchmode.com/" class="home">Website powered by Watchmode API</a>
      </div>
    </div>
  </div>
</template>

<style></style>
