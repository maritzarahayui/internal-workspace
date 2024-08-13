<template>
    <div class="flex flex-col items-center p-4">
      <h1 class="text-3xl font-bold mb-4">{{ msg }}</h1>
      <h2 v-if="user" class="text-xl mb-4">Signed In User: {{ user }}</h2>
  
      <div id="logout" v-if="isSignedIn" class="mb-4">
        <button @click="handleSignOut" class="px-4 py-2 bg-red-500 text-white rounded hover:bg-red-700 transition">logout</button>
      </div>
  
      <div id="GoogleSignIn" v-if="!isSignedIn" class="mt-4">
        <h3>Sign In with Google</h3>
        <button @click="handleSignInGoogle" class="px-4 py-2 bg-blue-500 text-white rounded hover:bg-blue-700 transition">login</button>
      </div>
    </div>
</template>
  
<script>
    import firebaseConfig from '../includes/firebase';
    import { getAuth, signInWithPopup, signOut, GoogleAuthProvider } from "firebase/auth";

    firebaseConfig

    const provider = new GoogleAuthProvider();
    const auth = getAuth();

    export default {
    name: 'Auth',
    props: {
        msg: String
    },
    data() {
        return {
        user: '',
        isSignedIn: false,
        }
    },
    methods: {
        handleSignInGoogle() {
        signInWithPopup(auth, provider)
            .then((result) => {          
            this.user = result.user.displayName;
            this.isSignedIn = true;
            }).catch((error) => {
            console.log(error);
            });
        },
        handleSignOut() {
        signOut(auth).then(() => {
            this.user = '';
            this.isSignedIn = false;
            }).catch((error) => {
            console.log(error);
            });
        }
    }
    }
</script>
  