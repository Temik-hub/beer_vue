<template>
    <div class="user__container">
      <div class="user__card">
        <div class="user__image">
          <img class="user__photo" :src="userAvatar()" alt="User photo">
        </div>
        <div class="user__data">
          <h3 class="user__name">{{user.first_name}}</h3>
          <p class="user__age">{{getFullYears()}} y.o.</p>
          <p class="user__employment">{{user.employment.title}}
            ({{user.employment.key_skill}})
          </p>
        </div>
      </div>
    </div>
</template>

<script>
export default {
  name: 'loadUser',
  data () {
    return {
      loading: false,
      bd: null,
      user: {"employment":{
        "title": "",
        "key_skill": ""}}
    }
  },
  methods: {
    fetchUser: function () {
      return fetch(`https://random-data-api.com/api/users/random_user`)
        .then(response => response.json())
        .then(json => this.user = json)
    },
    getFullYears: function () {
      const d = new Date(this.user.date_of_birth);
      const now = new Date()
      const addOne = now.getMonth() - d.getMonth() >= 0 && now.getDate() - d.getDate() >= 0
      const diff = now.getFullYear() - d.getFullYear()
      return diff - 1 + (addOne ? 1 : 0)
    },
    userAvatar: function () {
      return this.user.avatar
    }
    
  },
  computed: {},
  mounted() {
    this.fetchUser()
  }
}
</script>
