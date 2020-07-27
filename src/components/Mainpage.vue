<template>
  <div>



    <main>
      <div class="container mt-5 mb-3">
        <div class="row">

          <div class="offset-md-4  col-md-4 col-sm-12 px-sm-5 d-flex justify-content-between list-header  ">
            <div v-on:click="ispost = true" class="mousepointer">
              <i class="fas fa-th-large "></i>
              <span class="hidden md:inline"> Post</span>
            </div>

            <div class="mousepointer">
              <i class="far fa-square"></i>
              <span class="hidden md:inline"> igtv</span>
            </div>
              <div v-on:click="ispost = false" class="mousepointer">
              <i class="fas fa-user"></i>
              <span class="hidden md:inline"> Tagged</span>
              </div>

          </div>
        </div>
      </div>



      <div class="container">

        <div v-if="ispost === true" class="gallery">

          <div class="gallery-item" @click="toggleModal(index)" tabindex="0" v-for="(value,index) in list " :key="index">

            <img :src=value.url class="gallery-image" alt="">

            <div class="gallery-item-info">

              <ul>
                <li class="gallery-item-likes"><span class="visually-hidden">Likes:</span><i class="fas fa-heart" aria-hidden="true"></i> {{value.like}}</li>
                <li class="gallery-item-comments"><span class="visually-hidden">Comments:</span><i class="fas fa-comment" aria-hidden="true"></i> {{value.comment}}</li>
              </ul>

            </div>

          </div>

        </div>

        <div v-if="ispost === false" class="gallery">

          <div class="gallery-item" @click="toggleModal(index)" tabindex="0" v-for="(value,index) in tagged" :key="index">

            <img :src=value.url  class="gallery-image" alt="">

            <div class="gallery-item-info">

              <ul>
                <li class="gallery-item-likes"><span class="visually-hidden">Likes:</span><i class="fas fa-heart" aria-hidden="true"></i> {{value.like}}</li>
                <li class="gallery-item-comments"><span class="visually-hidden">Comments:</span><i class="fas fa-comment" aria-hidden="true"></i> {{value.comment}}</li>
              </ul>

            </div>

          </div>

        </div>




      </div>
      <!-- End of container -->

      <div>


        <b-modal id="modal-1" ref="my-modal" centered  hide-footer="hideFH" hide-header="hideFH" title="BootstrapVue">
          <div class="mb-5">
          <img v-on:dblclick="toggleLike(this)" :src=modeldata.url class="gallery-image" alt="">
          </div>

          <div  class="d-inline-flex mr-1 mousepointer" v-on:click="toggleLike(this)">
            <svg v-if="modeldata.islike === true" aria-label="Unlike" class="_8-yf5 " fill="#ed4956" height="24"
                 viewBox="0 0 48 48" width="24">
              <path d="M34.6 3.1c-4.5 0-7.9 1.8-10.6 5.6-2.7-3.7-6.1-5.5-10.6-5.5C6 3.1 0 9.6 0 17.6c0 7.3 5.4 12 10.6 16.5.6.5 1.3 1.1 1.9 1.7l2.3 2c4.4 3.9 6.6 5.9 7.6 6.5.5.3 1.1.5 1.6.5s1.1-.2 1.6-.5c1-.6 2.8-2.2 7.8-6.8l2-1.8c.7-.6 1.3-1.2 2-1.7C42.7 29.6 48 25 48 17.6c0-8-6-14.5-13.4-14.5z"></path>
            </svg>
          </div>
          <div  class="d-inline-flex mr-1 mousepointer" v-on:click="toggleLike(this)">
            <svg v-if="modeldata.islike === false" aria-label="Like" class="_8-yf5 " fill="#262626" height="24"
                 viewBox="0 0 48 48" width="24">
              <path d="M34.6 6.1c5.7 0 10.4 5.2 10.4 11.5 0 6.8-5.9 11-11.5 16S25 41.3 24 41.9c-1.1-.7-4.7-4-9.5-8.3-5.7-5-11.5-9.2-11.5-16C3 11.3 7.7 6.1 13.4 6.1c4.2 0 6.5 2 8.1 4.3 1.9 2.6 2.2 3.9 2.5 3.9.3 0 .6-1.3 2.5-3.9 1.6-2.3 3.9-4.3 8.1-4.3m0-3c-4.5 0-7.9 1.8-10.6 5.6-2.7-3.7-6.1-5.5-10.6-5.5C6 3.1 0 9.6 0 17.6c0 7.3 5.4 12 10.6 16.5.6.5 1.3 1.1 1.9 1.7l2.3 2c4.4 3.9 6.6 5.9 7.6 6.5.5.3 1.1.5 1.6.5.6 0 1.1-.2 1.6-.5 1-.6 2.8-2.2 7.8-6.8l2-1.8c.7-.6 1.3-1.2 2-1.7C42.7 29.6 48 25 48 17.6c0-8-6-14.5-13.4-14.5z"></path>
            </svg>
          </div>
            <div  class="d-inline-flex mr-1">
            <svg aria-label="Comment" class="_8-yf5 " fill="#262626" height="24" viewBox="0 0 48 48" width="24">
              <path clip-rule="evenodd"
                    d="M47.5 46.1l-2.8-11c1.8-3.3 2.8-7.1 2.8-11.1C47.5 11 37 .5 24 .5S.5 11 .5 24 11 47.5 24 47.5c4 0 7.8-1 11.1-2.8l11 2.8c.8.2 1.6-.6 1.4-1.4zm-3-22.1c0 4-1 7-2.6 10-.2.4-.3.9-.2 1.4l2.1 8.4-8.3-2.1c-.5-.1-1-.1-1.4.2-1.8 1-5.2 2.6-10 2.6-11.4 0-20.6-9.2-20.6-20.5S12.7 3.5 24 3.5 44.5 12.7 44.5 24z"
                    fill-rule="evenodd"></path>
            </svg>
          </div>
              <div  class="d-inline-flex mr-1">
            <svg aria-label="Share Post" class="_8-yf5 " fill="#262626" height="24" viewBox="0 0 48 48" width="24">
              <path d="M47.8 3.8c-.3-.5-.8-.8-1.3-.8h-45C.9 3.1.3 3.5.1 4S0 5.2.4 5.7l15.9 15.6 5.5 22.6c.1.6.6 1 1.2 1.1h.2c.5 0 1-.3 1.3-.7l23.2-39c.4-.4.4-1 .1-1.5zM5.2 6.1h35.5L18 18.7 5.2 6.1zm18.7 33.6l-4.4-18.4L42.4 8.6 23.9 39.7z"></path>
            </svg>
          </div>
        </b-modal>
      </div>
    </main>
  </div>
</template>

<script>
  import Vue from 'vue'
  import { BootstrapVue } from 'bootstrap-vue'
  import 'bootstrap/dist/css/bootstrap.css'
  import 'bootstrap-vue/dist/bootstrap-vue.css'
  import '../assets/css/main.css'

  Vue.use(BootstrapVue)
export default {

  name: 'Mainpage',
  data: function () {
    return {
      ispost:true,
      mainkey:'list',
      hideFH: false,
      modeldata: {},
      modeldatakey: 0,
      likesCount: 12,
     list:[
       {
         url:'../assets/images/posts/image1.jpg',
         like:56,
         comment:2,
         islike:true
       },
       {
         url:'../assets/images/posts/image2.jpg',
         like:56,
         comment:2,
         islike:true
       },
       {
         url:'../assets/images/posts/image3.jpg',
         like:56,
         comment:2,
         islike:true
       },
       {
         url:'../assets/images/posts/image4.jpg',
         like:56,
         comment:2,
         islike:true
       },
       {
         url:'../assets/images/posts/image5.jpg',
         like:56,
         comment:2,
         islike:true
       },
       {
         url:'../assets/images/posts/image6.jpg',
         like:56,
         comment:2,
         islike:true
       },
       {
         url:'../assets/images/posts/image1.jpg',
         like:56,
         comment:2,
         islike:true
       },
       {
         url:'../assets/images/posts/image2.jpg',
         like:56,
         comment:2,
         islike:true
       },



     ],

      tagged:[
        {
          url:'../assets/images/tagged/image1.jpg',
          like:56,
          comment:2,
          islike:true
        },
        {
          url:'../assets/images/tagged/image2.jpg',
          like:56,
          comment:2,
          islike:true
        }

      ]
    }
  },
  methods: {

    toggleModal(key) {

      this.mainkey = this.ispost === true?'list':'tagged';

      this.modeldata = this[this.mainkey][key];
      this.modeldatakey = key;
      this.$refs['my-modal'].toggle('#toggle-btn')
    },
    toggleLike: function()
    {

      if (this[this.mainkey][this.modeldatakey].islike === true) {
        this[this.mainkey][this.modeldatakey].like = this[this.mainkey][this.modeldatakey].like - 1;
        this[this.mainkey][this.modeldatakey].islike = false;
      } else {
        this[this.mainkey][this.modeldatakey].like = this[this.mainkey][this.modeldatakey].like + 1;
        this[this.mainkey][this.modeldatakey].islike = true;
      }

    },



  }

}
</script>
<style>

  :root {
    font-size: 10px;
  }

  *,
  *::before,
  *::after {
    box-sizing: border-box;
  }

  body {
    font-family: "Open Sans", Arial, sans-serif;
    min-height: 100vh;
    background-color: #fafafa;
    color: #262626;
    padding-bottom: 3rem;
  }

  img {
    display: block;
  }

  .container {
    max-width: 93.5rem;
    margin: 0 auto;
    padding: 0 2rem;
  }

  .btn {
    display: inline-block;
    font: inherit;
    background: none;
    border: none;
    color: inherit;
    padding: 0;
    cursor: pointer;
  }

  .btn:focus {
    outline: 0.5rem auto #4d90fe;
  }

  .visually-hidden {
    position: absolute !important;
    height: 1px;
    width: 1px;
    overflow: hidden;
    clip: rect(1px, 1px, 1px, 1px);
  }


  /* Gallery Section */

  .gallery {
    display: inline-flex;
    flex-wrap: wrap;
    margin: -1rem -1rem;
    padding-bottom: 3rem;
  }

  .gallery-item {
    position: relative;
    flex: 1 0 22rem;
    margin: 1rem;
    color: #fff;
    cursor: pointer;
    max-height: 270px;
    max-width: 270px !important;
  }

  .gallery-item:hover .gallery-item-info,
  .gallery-item:focus .gallery-item-info {
    display: flex;
    justify-content: center;
    align-items: center;
    position: absolute;
    top: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.3);
  }

  .gallery-item-info {
    display: none;
  }

  .gallery-item-info li {
    display: inline-block;
    font-size: 1.7rem;
    font-weight: 600;
  }

  .gallery-item-likes {
    margin-right: 2.2rem;
  }

  .gallery-item-type {
    position: absolute;
    top: 1rem;
    right: 1rem;
    font-size: 2.5rem;
    text-shadow: 0.2rem 0.2rem 0.2rem rgba(0, 0, 0, 0.1);
  }

  .fa-clone,
  .fa-comment {
    transform: rotateY(180deg);
  }

  .gallery-image {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  /* Loader */

  .loader {
    width: 5rem;
    height: 5rem;
    border: 0.6rem solid #999;
    border-bottom-color: transparent;
    border-radius: 50%;
    margin: 0 auto;
    animation: loader 500ms linear infinite;
  }

  /* Media Query */

  @media screen and (max-width: 40rem) {
    .profile {
      display: flex;
      flex-wrap: wrap;
      padding: 4rem 0;
    }

    .profile::after {
      display: none;
    }

    .profile-image,
    .profile-user-settings,
    .profile-bio,
    .profile-stats {
      float: none;
      width: auto;
    }

    .profile-image img {
      width: 7.7rem;
    }

    .profile-user-settings {
      flex-basis: calc(100% - 10.7rem);
      display: flex;
      flex-wrap: wrap;
      margin-top: 1rem;
    }

    .profile-user-name {
      font-size: 2.2rem;
    }

    .profile-edit-btn {
      order: 1;
      padding: 0;
      text-align: center;
      margin-top: 1rem;
    }

    .profile-edit-btn {
      margin-left: 0;
    }

    .profile-bio {
      font-size: 1.4rem;
      margin-top: 1.5rem;
    }

    .profile-edit-btn,
    .profile-bio,
    .profile-stats {
      flex-basis: 100%;
    }

    .profile-stats {
      order: 1;
      margin-top: 1.5rem;
    }

    .profile-stats ul {
      display: flex;
      text-align: center;
      padding: 1.2rem 0;
      border-top: 0.1rem solid #dadada;
      border-bottom: 0.1rem solid #dadada;
    }

    .profile-stats li {
      font-size: 1.4rem;
      flex: 1;
      margin: 0;
    }

    .profile-stat-count {
      display: block;
    }
  }

  /* Spinner Animation */

  @keyframes loader {
    to {
      transform: rotate(360deg);
    }
  }

  /*

  The following code will only run if your browser supports CSS grid.

  Remove or comment-out the code block below to see how the browser will fall-back to flexbox & floated styling.

  */

  @supports (display: grid) {
    .profile {
      display: grid;
      grid-template-columns: 1fr 2fr;
      grid-template-rows: repeat(3, auto);
      grid-column-gap: 3rem;
      align-items: center;
    }

    .profile-image {
      grid-row: 1 / -1;
    }

    .gallery {
      display: inline-flex;
      grid-template-columns: repeat(auto-fit, minmax(22rem, 1fr));
      grid-gap: 2rem;
    }

    .profile-image,
    .profile-user-settings,
    .profile-stats,
    .profile-bio,
    .gallery-item,
    .gallery {
      width: auto;
      margin: 0;
    }

    @media (max-width: 40rem) {
      .profile {
        grid-template-columns: auto 1fr;
        grid-row-gap: 1.5rem;
      }
      .gallery{
        justify-content: center;
      }

      .profile-image {
        grid-row: 1 / 2;
      }

      .profile-user-settings {
        display: grid;
        grid-template-columns: auto 1fr;
        grid-gap: 1rem;
      }

      .profile-edit-btn,
      .profile-stats,
      .profile-bio {
        grid-column: 1 / -1;
      }

      .profile-user-settings,
      .profile-edit-btn,
      .profile-settings-btn,
      .profile-bio,
      .profile-stats {
        margin: 0;
      }
    }
  }

  .list-header{
    font-family: "Open Sans", Arial, sans-serif;
    font-size: 14px ;

  }
  .gallery-item-info ul{
    padding:0 ;
  }
.mousepointer{
  cursor: pointer;
}

</style>
