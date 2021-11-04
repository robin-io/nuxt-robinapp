<template>
  <RobinChat 
  :api-key="'NT-CDuBlRKXV....PcGPMBnwHaoYbW'"
  :user-token="user_token"
  :user-name="user_name"
  :users="users"
  :keys="keys"
  :page-loader="true"
  />
</template>

<script>
// if the app keeps loading, please confirm you have the correct user_token and api_key
export default {
  name: 'Chat',
  data() {
    return {
      user_token: 'JUevyX.....AStMSrXR',
      user_name: 'Elvis Chuks',
      users:[],
      keys:{
				userToken: 'user_token',
        profileImage: 'profile_image',
        userName: 'fullname'
		  }
    }
  },
  methods: {
    getUsers() {
      fetch('https://your-api/endpoint/for/getting/all/users')
      .then(resp => resp.json())
      .then(data => {
        if (!data.error) {
          this.users = data.users
          /* 
          notice how the keys in the response object, align with the values in the keys prop
          {
            error : false,
            users: [
              {
                'user_token': 'asdsfa;sds',
                'profile_image: 'https://some-url.com/photo.png',
                'fullname': 'Michael Jordan'
                '
              },
              {
                'user_token': 'asdsfa;sds',
                'profile_image: 'https://some-url.com/photo.png',
                'fullname': 'Lebron James'
                '
              },
            ]
          }
          */
        }
      })
    }
  }
}
</script>
