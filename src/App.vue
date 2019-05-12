<template>
  <div id="activitybook">
    <nav class="navbar is-white topNav">
      <div class="container">
        <div class="navbar-brand">Activity Book</div>
      </div>
    </nav>
    <nav class="navbar is-white">
      <div class="container">
        <div class="navbar-menu">
          <a class="navbar-item" href="#">Newest</a>
          <a class="navbar-item" href="#">In Progress</a>
          <a class="navbar-item" href="#">Finished</a>
        </div>
      </div>
    </nav>
    <section class="container">
      <div class="columns">
        <div class="column is-3">
          <a
            v-if="!isFormDisplayed"
            @click="toggleFormDisplay"
            class="button is-primary is-block is-alt is-large"
            href="#"
          >New Activity</a>
          <div v-if="isFormDisplayed" class="create-form">
            <h2 class="formDisplay-Heading">Enter Your Activity</h2>
            <br>
            <form>
              <div class="field">
                <label class="label">Title</label>
                <div class="control">
                  <input
                    v-model="newActivity.title"
                    class="input"
                    type="text"
                    placeholder="Read a Book"
                  >
                </div>
              </div>
              <div class="field">
                <label class="label">Notes</label>
                <div class="control">
                  <textarea
                    v-model="newActivity.notes"
                    class="textarea"
                    placeholder="Write some notes here"
                  ></textarea>
                </div>
              </div>
              <div class="field is-grouped">
                <div class="control">
                  <button @click="createActivity" class="button is-link">Create Activity</button>
                </div>
                <div class="control">
                  <button @click="toggleFormDisplay" class="button is-text">Cancel</button>
                </div>
              </div>
            </form>
          </div>
        </div>
        <div class="column is-9">
          <div class="box content">
            <activity-item v-for="activity in activities" :activity="activity" :key="activity.id"></activity-item>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>
<script>
import ActivityItem from "./components/activityItems";
export default {
  name: "app",
  components: {
    ActivityItem
  },
  data() {
    return {
      isFormDisplayed: false,
      message: "Hello Vue!",
      titleMessage: "Title Message Vue!!!!!",
      isTextDisplayed: true,
      newActivity: {
        title: "",
        notes: ""
      },
      items: { 1: { name: "Filip" }, 2: { name: "John" } },
      user: {
        name: "Neils Hansan",
        id: "-Aj34jknvncx98812"
      },
      activities: {
        "1546968934": {
          id: "1546968934",
          title: "Learn Vue.js",
          notes: "I started today and it was not good.",
          progress: 0,
          category: "1546969049",
          createdAt: 1546969144391,
          updatedAt: 1546969144391
        },
        "1546969212": {
          id: "1546969212",
          title: "Read Witcher Books",
          notes: "These books are super nice",
          progress: 0,
          category: "1546969049",
          createdAt: 1546969144391,
          updatedAt: 1546969144391
        }
      },
      categories: {
        "1546969049": { text: "books" },
        "1546969225": { text: "movies" }
      }
    };
  },
  methods: {
    toggleTextDisplay() {
      this.isTextDisplayed = !this.isTextDisplayed;
    },
    toggleFormDisplay() {
      this.isFormDisplayed = !this.isFormDisplayed;
    },
    createActivity() {
      console.log(this.newActivity);
    }
  }
};
</script>

<style>
#activitybook {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
html,
body {
  font-family: "Open Sans", serif;
  background: #100e17;
}
footer {
  background-color: #f2f6fa !important;
}

.example-wrapper {
  margin-left: 30px;
}

.topNav {
  border-top: 5px solid #da1b60;
}
.topNav .container {
  border-bottom: 1px solid #e6eaee;
}
.navbar-brand {
  text-align: center;
  margin-top: 20px;
  font-family: "Monoton", cursive;
  color: #da1b60;
  padding: 11px 0px;
  font-size: 62px;
  background: -webkit-linear-gradient(#eee, rgb(26, 25, 25));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}
.formDisplay-Heading {
  text-align: center;
  background: linear-gradient(to bottom, #ff8a00, #da1b60);
  padding: 10px;
  color: #ffffff;
  font-weight: bold;
}
.container .columns {
  margin: 3rem 0;
}
.navbar-menu .navbar-item {
  padding: 0 2rem;
}
.navbar-menu .navbar-item:hover {
  background: linear-gradient(to bottom, #ff8a00, #da1b60);
  color: white;
}

.field .label {
  color: aliceblue;
}
aside.menu {
  padding-top: 3rem;
}
aside.menu .menu-list {
  line-height: 1.5;
}
aside.menu .menu-label {
  padding-left: 10px;
  font-weight: 700;
}
.button.is-primary.is-alt {
  background: #da1b60;
  background: -webkit-linear-gradient(to bottom, #ff8a00, #da1b60);
  background: linear-gradient(to bottom, #ff8a00, #da1b60);
  font-weight: 700;
  font-size: 14px;
  height: 3rem;
  line-height: 2.8;
}
.button.is-link {
  background: -webkit-linear-gradient(to bottom, #568d56, #5daf0f);
  background: linear-gradient(to bottom, #568d56, #5daf0f);
  border-color: transparent;
  color: #fff;
}
.button.is-link:hover {
  background: -webkit-linear-gradient(to bottom, #2c642c, #28460c);
  background: linear-gradient(to bottom, #2c642c, #28460c);
  border-color: transparent;
  color: #fff;
}
.button.is-text {
  background-color:rgb(104, 104, 233);
  border-color: transparent;
  color:rgb(224, 223, 217);
  text-decoration: underline;
}

.button.is-text:hover {
  background-color:rgb(9, 9, 155);
  color:rgb(240, 239, 238);
}
.media-left img {
  border-radius: 50%;
}
.media-content p {
  font-size: 14px;
  line-height: 2.3;
  font-weight: 700;
  color: #8f99a3;
}
article.post {
  margin: 1rem;
  padding-bottom: 1rem;
  border-bottom: 1px solid #e6eaee;
}
article.post:last-child {
  padding-bottom: 0;
  border-bottom: none;
}
.menu-list li {
  padding: 5px;
}

.navbar-brand > h1 {
  font-size: 31px;
  padding: 20px;
}
</style>
