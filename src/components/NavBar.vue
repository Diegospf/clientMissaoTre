<template>
  <div th:fragment="logo">
    <div class="logo-container p-3 d-flex">
        <div style="margin-right: 20px;">
            <a href="/"><img class="img-fluid" style="max-width: 100px;" src="../assets/tre-pe.png"></a>
        </div>
        <div class="col-8 col-xl-11 col-lg-10 col-md-9 align-middle">
            <span class="logo">Consultas de Unidades Eleitorais</span>
        </div>
    </div>
    <nav class="navbar navbar-expand-lg bg-success mb-4">
        <div class="container-fluid">
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse navegacao" id="navbarNav">
                <ul class="navbar-nav">
                    <li class="nav-item">
                        <a class="nav-link colorir" style="cursor: pointer;" @click='mudarTipo("Zona")'>Zona</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link colorir" style="cursor: pointer;" @click='mudarTipo("Município")'>Município</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link colorir" style="cursor: pointer;" @click='mudarTipo("Polo")'>Polo</a>
                    </li>
                </ul>
            </div>
        </div>
    </nav>
</div>
</template>

<script>
export default {
  name: 'NavBar',
  data () {
    return {
      tipo: "Zona"
    }
  },
  methods:{
    mudarTipo(tipo) {
        this.$emit('mudarTipo', tipo)
   }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .logo-container {
    background-color: #006600;
    color: #FFF;
  }

  .logo {
      font-family: 'Ubuntu', sans-serif;
      font-size: 2.5em;
      line-height:2;
      color: #FFFFFF;
  }

  .logo a:hover, a:visited, a:link, a:active {
    text-decoration: none;
}

.colorir{
  color: white;
}
.colorir:hover{
    color: yellow;
    transition-duration: .5s;
}

  @media only screen and (max-width: 850px) {
    .logo{
       font-size: 30px;
       line-height:2.5;
    }
}

@media only screen and (max-width: 720px) {
    .logo{
       font-size: 19px;
       line-height:3.7;
    }
}
</style>
