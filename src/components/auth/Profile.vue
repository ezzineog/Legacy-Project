<template>
  <div class="container emp-profile">
    <div>
      <div class="row">
        <div class="col-md-4">
          <div class="profile-img">
            <img
              src="https://civilcode.ge/images/2/24/Blank-avatar.png"
              alt=""
            />
            <div class="file btn btn-lg btn-primary">
              Change Photo
              <input
                type="file"
                name="file"
                @change="onFileSelect"
                ref="file"
              />
            </div>
            <button @click="uploadImage">uploadImage</button>
          </div>
        </div>
        <div class="col-md-6">
          <div class="profile-head">
            <h5>{{ users.last_name }} , {{ users.first_name }}</h5>
            <h6>
              job
            </h6>
            <p class="proile-rating">RANKINGS : <span>8/10</span></p>

            <ul class="nav nav-tabs" id="myTab" role="tablist">
              <li class="nav-item">
                <a
                  class="nav-link active"
                  id="home-tab"
                  data-toggle="tab"
                  href="#home"
                  role="tab"
                  aria-controls="home"
                  aria-selected="true"
                  >About</a
                >
              </li>
              <li class="nav-item">
                <a
                  class="nav-link"
                  id="profile-tab"
                  data-toggle="tab"
                  href="#profile"
                  role="tab"
                  aria-controls="profile"
                  aria-selected="false"
                  >Timeline</a
                >
              </li>
            </ul>
          </div>
        </div>
        <div class="col-md-2">
          <input
            type="submit"
            class="profile-edit-btn"
            name="btnAddMore"
            value="Edit Profile"
          />
        </div>
      </div>
      <div class="row">
        <div class="col-md-4">
          <div class="profile-work">
            <p>WORK LINK</p>
            <a href="">Website Link</a><br />
            <a href="">Bootsnipp Profile</a><br />
            <a href="">Bootply Profile</a>
            <p>SKILLS</p>
            <a href="">Web Designer</a><br />
            <a href="">Web Developer</a><br />
            <a href="">WordPress</a><br />
            <a href="">WooCommerce</a><br />
            <a href="">PHP, .Net</a><br />
          </div>
        </div>
        <div class="col-md-8">
          <div class="tab-content profile-tab" id="myTabContent">
            <div
              class="tab-pane fade show active"
              id="home"
              role="tabpanel"
              aria-labelledby="home-tab"
            >
              <div class="row">
                <div class="col-md-6">
                  <label>User Id</label>
                  <span>users-{{ users.id }}</span>
                </div>
                <div class="col-md-6">
                  <p>{{ users.last_name }}</p>
                </div>
              </div>
              <div class="row">
                <div class="col-md-6">
                  <label>Name</label>
                </div>
                <div class="col-md-6">
                  <p>{{ users.first_name }}</p>
                </div>
              </div>
              <div class="row">
                <div class="col-md-6">
                  <label>Email</label>
                </div>
                <div class="col-md-6">
                  <p>{{ users.email }}</p>
                </div>
              </div>
            </div>
            <!-- <div
              class="tab-pane fade"
              id="profile"
              role="tabpanel"
              aria-labelledby="profile-tab"
            >
              <div class="row">
                <div class="col-md-6">
                  <label>Experience</label>
                </div>
                <div class="col-md-6">
                  <p>Expert</p>
                </div>
              </div>
              <div class="row">
                <div class="col-md-6">
                  <label>Hourly Rate</label>
                </div>
                <div class="col-md-6">
                  <p>10$/hr</p>
                </div>
              </div>
              <div class="row">
                <div class="col-md-6">
                  <label>Total Projects</label>
                </div>
                <div class="col-md-6">
                  <p>230</p>
                </div>
              </div>
              <div class="row">
                <div class="col-md-6">
                  <label>English Level</label>
                </div>
                <div class="col-md-6">
                  <p>Expert</p>
                </div>
              </div>
              <div class="row">
                <div class="col-md-6">
                  <label>Availability</label>
                </div>
                <div class="col-md-6">
                  <p>6 months</p>
                </div>
              </div>
              <div class="row">
                <div class="col-md-12">
                  <label>Your Bio</label><br />
                  <p>Your detail description</p>
                </div>
              </div>
            </div> -->
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// import axios from "axios";
export default {
  name: "Profile",
  data() {
    return {
      selectedFile: null,
      res: null
    };
  },
  mounted() {
    this.$store.commit("getData");
  },
  computed: {
    users: function() {
      return this.$store.state.usersData;
    }
  },
  methods: {
    onFileSelect() {
      this.selectedFile = this.$refs.file.files["0"];
      console.log("test", this.$refs.file.files["0"]);
    },
    async uploadImage() {
      console.log("uploadImage Clicked");
      // try {
      //   // const fd = new FormData();
      //   // fd.append("img", this.selectedFile);
      //   // console.log("fd", fd);
      //   const reader = new FileReader();
      //   reader.onload = e => {
      //     this.imgSrc = e.target.result;
      //     console.log("imgSrc", e.target.result);
      //   };
      //   reader.readAsDataURL(this.selectedFile);
      //   // console.log("reader", reader);
      //   await axios.put("/avatar/:id", reader);
      //   console.log("[client side] res");
      // } catch (err) {
      //   console.log(err);
      // }
    }
  }
};
</script>

<style scoped>
body {
  background: -webkit-linear-gradient(left, #3931af, #00c6ff);
}
.emp-profile {
  padding: 3%;
  margin-top: 3%;
  margin-bottom: 3%;
  border-radius: 0.5rem;
  background: #fff;
}
.profile-img {
  text-align: center;
}
.profile-img img {
  width: 70%;
  height: 100%;
}
.profile-img .file {
  position: relative;
  overflow: hidden;
  margin-top: -20%;
  width: 70%;
  border: none;
  border-radius: 0;
  font-size: 15px;
  background: #212529b8;
}
.profile-img .file input {
  position: absolute;
  opacity: 0;
  right: 0;
  top: 0;
}
.profile-head h5 {
  color: #333;
}
.profile-head h6 {
  color: #0062cc;
}
.profile-edit-btn {
  border: none;
  border-radius: 1.5rem;
  width: 70%;
  padding: 2%;
  font-weight: 600;
  color: #6c757d;
  cursor: pointer;
}
.proile-rating {
  font-size: 12px;
  color: #818182;
  margin-top: 5%;
}
.proile-rating span {
  color: #495057;
  font-size: 15px;
  font-weight: 600;
}
.profile-head .nav-tabs {
  margin-bottom: 5%;
}
.profile-head .nav-tabs .nav-link {
  font-weight: 600;
  border: none;
}
.profile-head .nav-tabs .nav-link.active {
  border: none;
  border-bottom: 2px solid #0062cc;
}
.profile-work {
  padding: 14%;
  margin-top: -15%;
}
.profile-work p {
  font-size: 12px;
  color: #818182;
  font-weight: 600;
  margin-top: 10%;
}
.profile-work a {
  text-decoration: none;
  color: #495057;
  font-weight: 600;
  font-size: 14px;
}
.profile-work ul {
  list-style: none;
}
.profile-tab label {
  font-weight: 600;
}
.profile-tab p {
  font-weight: 600;
  color: #0062cc;
}
</style>
