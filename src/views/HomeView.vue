<template>
  <div class="home">
    <div class="col-md-7 col-sm-12 col-md-offset-5 main-content">
      <section>
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
      </section>
    </div>
  </div>
</template>

<style></style>

<script>
const axios = require("axios");

export default {
  data: function () {
    return {
      articles: [],
      teamFilter: "",
    };
  },
  created: function () {
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
