<template>
  <div class="bloc">
    <profileInfoC :infoUser="this.infoUser"></profileInfoC>
    <div class="col left">
      <addPostC></addPostC>
    </div>
    <div class="posts">
      <h1>Mis publicaciones</h1>
    </div>
  </div>
</template>
<script type="text/javascript">
import profileInfoC from '~/components/profile/profileInfoC'
import addPostC from '~/components/profile/addPostC'
import { mapGetters, mapActions } from 'vuex'
export default {
  data () {
    return {
      staticImg: require('~/assets/images/profile.jpg'),
      followText: 'Seguir',
      following: false,
      fullStar: '&#xe838;',
      emptyStar: '&#xe83a;'
    }
  },
  methods: {
    ...mapActions(['bindAuth']),
    follow () {
      if (this.following) {
        this.following = false
        this.followText = 'Seguir'
      } else {
        this.following = true
        this.followText = 'Dejar de seguir'
      }
    },
    showStar () {
      if (this.following) {
        return this.fullStar
      } else {
        return this.emptyStar
      }
    },
    showImg () {
      return 'background-image: url(' + this.infoUser.src + ')'
    }
  },
  components: {
    addPostC,
    profileInfoC
  },
  computed: {
    ...mapGetters({ infoUser: 'getProfile' })
  }
}
</script>
<style scoped lang='scss'>
@import "assets/sass/colors.scss";

.posts {
  width:100%;
  padding:10px;
  margin-bottom:-3%;
}
.align {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
textarea {
  width: 100%;
  padding: 10px;
}

.info {
  width: 100%;
}
p{
  font-weight: 100;
}

.conditions { display: flex;align-items: center;}

.ico {
  margin-left: 10px;
}

h1 {
  color: $redColor;
  margin-bottom: 4%;
}
h5 {
  font-weight:200;
  margin-top: 10px;
  font-size: 16px;
  background-color: #DBE5E6;
  padding: 5px;
  border-bottom-left-radius: 10px;
}

h4 {
  color: #525252;
}

img{width: 100%;}


.bloc {
  width: 100%;
  margin-top: 2%;
}
.col {
  padding: 20px;
  width: 100%;
  border-top:1px solid #E9E9E9;
}

.cel {
  padding: 10px;
  width: 100%;
}

input {
  width: 85%;
  height: 40px;
  padding: 5px;
}

.imgp {
  max-width: 200px;
}

div.avatar {
    height: 200px;
    width: 200px;
    background-repeat: no-repeat;
    background-position: 50%;
    background-size: 100% auto;
    background-color: white;
}

.pen {
  color: #E5BE5C;
  display: inline-block;
  padding-top: 2%;
}

@media screen and (min-width: 750px) {

  .bloc {
    display: flex;
    flex-flow: row wrap;
  }

  .blocinf {
    display: flex;
    flex-flow: row wrap;
  }
  .col {
    width: 50%;
  }

  .cel {
    width: 100%;

  }
}

@media screen and (min-width: 1200px) {
  .cel {
    width: 50%;

  }
}

</style>
