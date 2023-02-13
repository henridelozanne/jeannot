<template>
  <section>
    <div class="hero">
      <h1>S'allier pour <span class="special">Avancer</span></h1>

      <h4>
        Le cabinet Autisme & Advice est un cabinet de conseil et d’accompagnement pour les structures, les familles ou les professionnels accompagnant les personnes avec autisme quel que soit l’âge.
      </h4>

      <div class="around">
        <SolutionSVG />
        <p>
          Evelyn : « Je suis psychologue clinicienne depuis plus de 10 ans avec 8 ans de spécialisation en autisme. Sensibilisée et supervisée à la pratique de l’ABA pendant 3 années, j’ai ensuite été formée pendant 3 ans et demi à la méthode SACCADE. Spécialiste de l’autisme, je mets en avant mes compétences de psychologue (test psychologique, entretien parentale, analyse du fonctionnement de la personne autiste, restitution sous forme de bilan…). J’essayerai de vous apporter soutien et écoute tout au long de notre alliance. »
        </p>
        <p>
          Jeanne : « Je suis éducatrice spécialisée depuis 7 ans, j’ai tout de suite été attirée par le milieu de l’autisme. Je me suis d’abord formée à la méthode ABA pendant 2 ans et ai été supervisée tout au long par une psychologue ABA- BCBA. J’ai ensuite été formée à la méthode SACCADE pendant 3 ans et demi. J’ai pu créer de nombreux supports afin d’apporter dans ma pratique une technicité propre à la complexité de l’autisme, alliant connaissance du terrain et analyse neurocognitive. Je tenterai alors de vous accompagner au mieux dans tout le suivi de prise en charge de votre enfant.»
        </p>
      </div>

      <div class="around-2">
        <ToySVG />
        <p>Suite à notre collaboration de 5 années, nous avons décidé de continuer l’aventure ensemble car c’est dans la complémentarité de nos métiers et de nos connaissances qu’il nous a semblé avoir les meilleurs résultats.</p>
        <p>Le cabinet Autism & Advice met un point d'honneur à suivre les recommandations de l' <a target="_blank" href="https://www.has-sante.fr/">HAS</a>.</p>
        <p>
          Afin de mieux accompagner, le cabinet A&A met à votre disposition
          <router-link to="/auticto" class="auticto-word">
            <span>AUTICTO</span>
          </router-link>, la banque de pictogrammes adaptée aux personnes avec autisme.
        </p>
      </div>
    </div>
  </section>
</template>

<script>
import SolutionSVG from '../components/SolutionSVG.vue'
import ToySVG from '../components/ToySVG.vue'

export default {
  name: 'AutictoHero',

  components: {
    SolutionSVG,
    ToySVG
  }
}
</script>

<style lang="scss" scoped>
section {
  width: 100%;
  // padding: 0 10%;
  background-image: radial-gradient(circle farthest-corner at 10% 20%, rgba(234, 249, 249, 0.67) 0.1%, rgba(239, 249, 251, 0.63) 90.1%);

  .hero {
    margin: 0 auto;
    width: 80%;
    max-width: 1200px;
    padding: 60px 0;

    h1 {
      font-size: 32px;
      font-weight: 600;
      // color: #162a48;
      margin-bottom: 15px;
      background: -webkit-linear-gradient(rgb(46, 217, 166), rgb(46, 189, 217));
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      // border-bottom: 3px solid #162a48;
      // width: fit-content;
    }

    h4 {
      font-size: 24px;
      font-weight: 400;
      line-height: 1.2;
      color: #646668;
      margin: 0 auto 30px;
    }

    p {
      text-align: initial;
      line-height: 1.6rem;
    }

    p, a {
      color: #646668;
    }
  }

  @media screen and (max-width: 700px) {
    .hero {
      padding-bottom: 100px;
    }
  }

}

.new {
  display: flex;
  align-items: center;
  margin-top: 50px;

  > div {

    p:first-of-type {
      margin-top: 0;
    }
  }

  svg {
    min-width: 200px;
    margin-left: 50px;
  }
}

.new-2 {
  display: flex;
  align-items: center;
  margin-top: 50px;

  > div {

    p:first-of-type {
      margin-top: 0;
    }
  }

  svg {
    width: 400px;
    margin-right: 50px;
  }

}
.auticto-word {
  background: -webkit-linear-gradient(rgb(46, 217, 166), rgb(46, 189, 217));
  font-size: 1.2rem;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  position: relative;
  padding-bottom: 3px;

  &:hover::after {
            width: 100%;
            right: 0;
          }

          &::after {
            background: none repeat scroll 0 0 transparent;
            bottom: 0;
            content: "";
            display: block;
            height: 4px;
            right: 0;
            position: absolute;
            background: linear-gradient(to left, rgb(46, 217, 166), rgb(46, 189, 217) 100%);
            transition: width .5s ease 0s, right .5s ease 0s;
            width: 0;
            opacity: 0.5;
          }
}

@media screen and (max-width: 768px) {
  .new, .new-2 {
    svg {
      min-width: 150px;
      max-width: 150px;
    }
  }
}

.around {
  p {
    text-align: justify;
  }

  svg {
    float: right;
    margin: 0 0 20px 20px;
    // height: 150px;
    width: clamp(100px, 28%, 250px);
    max-height: 200px;
    // width: 110px;
  }

  @media screen and (max-width: 768px) {
    svg {
      margin: 0 auto 20px;
      width: 100%;
    }
  }
}

.around-2 {
  margin-top: 50px;

  p {
    text-align: justify;
  }

  svg {
    float: left;
    margin: 0 20px 20px 0;
    // height: 150px;
    width: clamp(100px, 28%, 250px);
    max-height: 200px;
  }

  @media screen and (max-width: 768px) {
    svg {
      margin: 0 auto 20px;
      width: 100%;
    }
  }
}
</style>
