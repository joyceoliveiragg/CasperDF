<template>
  <div class="categorias">
    <h2>{{noticia.categoria}}</h2> 
      <div class="center">
          <div class="property-card">
          <a href="#">
            <div class="property-image">
              <img :src="noticia.imagem">
              <div class="property-image-title">
                <!-- Optional <h5>Card Title</h5> If you want it, turn on the CSS also. -->
              </div>
            </div></a>
          <div class="property-description">
            <h5> {{noticia.titulo}} </h5>
            <p>{{noticia.descricao}}</p>
          </div>
        </div>

      </div>
  </div>    
</template>

<script>
export default {
    nome: 'Cartao',
    props:{
      noticia: {
        type: Object,
        default:{
          titulo:'',
          descricao:'',
          imagem: '',
          categoria:''
        }
    }
    }

}

</script>

<style>
    body
{
 
  font-family: 'RobotoDraft', 'Roboto', sans-serif;
  -webkit-font-smoothing: antialiased;
}

*
{
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
}
.categorias
{
  margin-bottom: 10%;
      display: flex;
    align-items: center;
    flex-direction: column;

}
.h2{
      margin: 15px;
    font-size: 1.4em;
    font-weight: 700;
}
h5
{
  margin:0px;
  font-size:1.4em;
  font-weight:700;
}

p
{
  font-size:12px;
}

.center
{display: flex;
    height: 100vh;
    width: 100%;
    flex-wrap: wrap;
    flex-direction: row;
    align-content: flex-start;
    justify-content: space-around;
    align-items: center;
}

/* End Non-Essential  */

.property-card
{
  height:18em;
  width:14em;
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:vertical;
  -webkit-box-direction:normal;
  -ms-flex-direction:column;
  flex-direction:column;
  position:relative;
  
  border-radius:16px;
  overflow:hidden;
  -webkit-box-shadow:  15px 15px 27px #e1e1e3, -15px -15px 27px #ffffff;
  box-shadow:  15px 15px 27px #e1e1e3, -15px -15px 27px #ffffff;
}
/* ^-- The margin bottom is necessary for the drop shadow otherwise it gets clipped in certain cases. */

/* Top Half of card, image. */

.property-image
{
  height:6em;
  width:14em;
  padding:1em 2em;
  position:Absolute;
  top:0px;
  
 /* background-image:url('https://cdn.photographylife.com/wp-content/uploads/2017/01/What-is-landscape-photography.jpg');*/
  background-size:cover;
  background-repeat:no-repeat;
}

/* Bottom Card Section */

.property-description
{
  background-color: #FAFAFC;
  height:12em;
  width:14em;
  position:absolute;
  bottom:0em;
 

  padding: 0.5em 1em;
  text-align:center;
}

/* Social Icons */

.property-social-icons
{
  width:1em;
  height:1em;
  background-color:black;
  position:absolute;
  bottom:1em;
  left:1em;
  
}

/* Property Cards Hover States */

.property-card:hover .property-description
{
  height:0em;
  padding:0px 1em;
}
.property-card:hover .property-image
{
  height:18em;
}

.property-card:hover .property-social-icons
{
  background-color:white;
}

.property-card:hover .property-social-icons:hover
{
  background-color:blue;
  cursor:pointer;
}


</style>