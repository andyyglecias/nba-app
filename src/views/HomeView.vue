<template>
  <div class="home">
    <noscript>
      <div class="no-js-menu">
        <ul>
          <li><i class="fa fa-home"></i><a href="index.html">Home</a></li>
          <li>
            <i class="fa fa-user"></i><a href="author.html">John Smith</a>
          </li>
          <li><i class="fa fa-anchor"></i><a href="page.html">About</a></li>
          <li>
            <i class="fa fa-star"></i><a href="favorites.html">Favorites</a>
          </li>
          <li>
            <i class="fa fa-paper-plane"></i><a href="contact.html">Contact</a>
          </li>
          <li><i class="fa fa-file"></i><a href="post.html">Post Page</a></li>
          <li>
            <i class="fa fa-home"></i><a href="alt-home.html">Alternate Home</a>
          </li>
          <li>
            <i class="fa fa-image"></i><a href="category.html">Category Page</a>
          </li>
        </ul>
      </div>
    </noscript>
    <!-- end no script -->

        <section class="col-md-7 col-sm-12 col-md-offset-5 main-content">
          <div class="sub-nav">
            <a href="#" class="select-posts active">Posts</a>
          </div>

          <div class="home-page-posts animated fadeIn">
            <article v-for="article in articles" class="post">
              <div class="post-preview col-xs-10 no-gutter">
                <h2>
                  {{ article.title }}
                </h2>

                <h4><a v-bind:href="article.url">Read Full Article</a></h4>

                <p class="meta">
                  Source:
                  {{ article.source }}
                  <i class="link-spacer"></i> <i class="fa fa-bookmark"></i> 6
                  minute read
                </p>
              </div>

              <div class="col-xs-2 no-gutter">
                <img
                  src="img/basketball-2.jpg"
                  class="user-icon"
                  alt="user-image"
                />
              </div>
            </article>
          </div>
          <!-- Home page posts -->

          <footer class="split-footer">
            <a href="post.html">Chicago Bulls</a>
            <i class="link-spacer"></i>
            <a href="post.html">Latest News</a>
          </footer>
        </section>
        <!-- main content -->
      </div>
      <!--/row -->
    </main>
    <!-- /container -->
  </div>
</template>

<style></style>

<script>
const axios = require("axios");

export default {
  data: function () {
    return {
      articles: [],
    };
  },
  created: function () {},
  mounted: function () {
    const axios = require("axios");

    const options = {
      method: "GET",
      url: "https://nba-latest-news.p.rapidapi.com/news",
      headers: {
        "X-RapidAPI-Host": "nba-latest-news.p.rapidapi.com",
        "X-RapidAPI-Key": "d503e56faamshdb8474da44d9ec0p1416dbjsnb664c0606337",
      },
    };

    axios
      .request(options)
      .then((response) => {
        console.log(response.data);
        this.articles = response.data;
      })
      .catch(function (error) {
        console.error(error);
      });
  },
  methods: {},
  computed: {},
};
</script>
