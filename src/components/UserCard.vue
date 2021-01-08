<template>
  <div class="user-card">
    <div class="container">
      <div class="user-card__avatar-box">
        <Avatar />
      </div>
      <div class="user-card__user-info">
        <span class="user-card__fullName">{{ fullName }}</span>
        <span class="user-card__username">@{{ user.username }}</span>
        <p class="user-card__description">
          Soy un estudiante argentino de 3er año de la carrera de Diseño
          Multimedial. Me especializo en la edición y post-producción de
          material audiovisual, modelado 3D y desarollo web.
        </p>
        <div class="user-card__bottom-box">
          <span class="user-card__followers">Followers: {{ followers }}</span>
          <button class="user-card__button" @click="followUser">Follow</button>
        </div>
      </div>
    </div>
  </div>
  <PostList :username="user.username" />
</template>
<script>
import Avatar from "./Avatar";
import PostList from "./PostList";

export default {
  name: "UserCard", //El nombre del componente que estamos creando
  components: {
    Avatar,
    PostList,
  },
  data() {
    //Datos que vamos a utilizar de forma dinámica en el documento
    return {
      followers: 0,
      user: {
        id: 1,
        username: "tobicorradi",
        firstName: "Tobías",
        lastName: "Corradi",
        email: "corraditobias@gmail.com",
        isAdmin: true,
      },
    };
  },
  watch: {
    //Como useEffect, vigila si cambia algo
    followers(newFollowerCount, oldFollowerCount) {
      //Una vez que cambió 'followers' crea dos datos, uno que es como estaba el elemento antes de cambiar, y el otro es como se encuentra ahora
      if (oldFollowerCount < newFollowerCount) {
        //Si la cantidad de seguidres vieja es menor a la actual, le avisamos al usuario que ganó un seguidor
        console.log(`${this.user.username} has gained a follower`);
      }
    },
  },
  //No acepta argumentos, son utilizados por lo general para hacer cálculos y retornarlos.
  computed: {
    fullName() {
      return `${this.user.firstName} ${this.user.lastName}`; //This se utiliza para referencias el data()
    },
  },
  //Son functiones estáticas  hechas para REACCIONAR a eventos que suceden en el dom, y acepta argumentos.
  methods: {
    followUser() {
      this.followers++;
    },
  },
  //Hook que corre una vez que se carga el componente por primera vez
  mounted() {
    this.followUser();
  },
};
</script>

<style>
.user-card {
  background-color: rgb(255, 255, 255);
  padding: 30px;
}
.user-card span {
  display: block;
}
.user-card__user-info {
  width: 100%;
}
.user-card__avatar-box {
  margin-right: 15px;
}
.user-card__fullName {
  font-weight: bold;
  font-size: 24px;
  margin-bottom: 4px;
}
.user-card__admin-badge {
  background-color: #965df3;
  color: white;
  padding: 7px 15px;
  border-radius: 30px;
  display: inline-block;
}
.user-card > .container {
  display: flex;
  align-items: center;
}
.user-card__description {
  max-width: 430px;
  font-size: 13px;
  color: #959595;
  line-height: 21px;
  margin: 5px 0px;
}
.user-card__button {
  border: 2px solid #0080fb;
  color: #0080fb;
  padding: 10px 25px;
  background: transparent;
  border-radius: 40px;
  font-weight: bold;
}
.user-card__bottom-box {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
