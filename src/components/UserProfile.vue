<template>
    <div class = "user-profile">
        <div class = "user-profile__user-panel">
            
            <h1 class = "user-profile__username">@{{ user.userName }}</h1>
            
            <div class = "user-profile__admin-badge" v-if="user.isAdmin">
                Admin
            </div>

            <div class = "user-profile__follower-count">
                <strong> Followers: </strong> {{ followers }}
            </div>

            <form class="user-profile__create-twoot">
                <label for="newTwoot"><strong>New Twoot</strong></label>
                <textarea id="newTwoot" rows="4"/>
            </form> 
        </div>

                   
    
        <div class = "user-profile__twoots-wrapper">
           <TwootItem 
                v-for="twoot in user.twoots" 
                :key="twoot.id" 
                :userName="user.userName" 
                :twoot="twoot" 
                @favourite="toggleFavourite"
           />
        </div>
    </div>
</template>

<script>
import TwootItem from "./TwootItem.vue"

export default{
    name: "UserProfile",
    components : { TwootItem },
    data() {
        return {
            followers: 0,
            user: {
                //id: 1,
                userName: "Tamer_Khaled",
                firstName: "Tamer",
                lastName: "khaled",
                email: "tamerKhaled213@gmail.com",
                isAdmin: true,
                twoots: [
                    { id: 1, content: "twotter is done!" },
                    { id: 2, content: "don't forget to subscribe to that"}
                ]
            },

         /*   emails:[
                {id: 1, from: "khaled", to: "tamer", subject: "homework"},
                {id: 2, from: "khaled", to: "said", subject: "classwork"},
                {id: 3, form: "tamer", to: "said", subject: "nothing"}
            ]
*/

        }
    },
    
    watch: { // can be done for atomic var or computed one
        followers(newFollowerCount, oldFollowerCount){
            if (newFollowerCount > oldFollowerCount){
                console.log(`${this.user.userName} has gained a follower`);
            }
        }
    },

    computed: {
        fullName() {
            return `${this.user.firstName} ${this.user.lastName}`;
        }
    },

    methods: {
        followUser() {
            this.followers++;
        },

        toggleFavourite(id) {
            console.log('favourite tweet' + id);
        }
    },

    mounted(){
        this.followUser();
    }
    
};
</script>


<style scoped>
.user-profile {
    display: grid;
    grid-template-columns: 1fr 3fr;
    width: 100%;
    padding: 50px 5%;
}

.user-profile__user-panel {
    display: flex;
    flex-direction: column;
    margin-right: 50px;
    padding: 20px;
    background-color: white;
    border-radius: 5px;
    border: 1px solid #DFE3E8;
}
.user-profile__admin-badge {
    background: rebeccapurple;
    color: white;
    border-radius: 5px;
    margin-right: auto;
    padding: 0 10px;
    font-weight: bold;
    margin-top: 5px;
    margin-bottom: 5px;
    
}
.user-profile__create-twoot {
    border-top: 1px solid #DFE3E8;
    padding-top: 20px;
    display: flex;
    flex-direction: column;
}

.emailsWrapper {
    background:rgb(255, 255, 255);
    display: grid;
    width: 100%;  
    margin-right: 50px; 
}

.email {
     background: rgb(125, 189, 183);
    color: white;
    border-radius: 5px;
    margin-right: auto;
    padding: 0 10px;
    font-weight: bold;
    margin-top: 5px;
    margin-bottom: 5px;
}


h1 {
    margin: 0;
}
</style>