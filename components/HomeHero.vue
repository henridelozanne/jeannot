<template>
  <section>
    <div class="hero">
      <h1>S'allier pour avancer</h1>

      <h4>
        Le cabinet Autism & Advice est un cabinet de conseil et d’accompagnement pour les structures, les familles ou les professionnels accompagnant les personnes avec autisme quel que soit l’âge. <span>
          Afin de mieux accompagner, le cabinet A&A met à votre disposition
          <span class="auticto-word" @click="goToAuticto">AUTICTO</span>, la banque de pictogrammes adaptée aux personnes avec autisme.
        </span>
      </h4>

      <p class="auticto">
        <button @click="goToAuticto">
          Découvrir
        </button>
      </p>

      <div class="ctnr">
        <div class="temoignage-ctn evelyn">
          <SolutionSVG />
          <div class="say">
            <div class="job-ctn">
              <div class="dot" />
              <span class="job"><span class="first-name">Evelyn</span>, Psychologue clinicienne</span>
            </div>

            « Je suis psychologue clinicienne depuis plus de 10 ans avec 8 ans de spécialisation en autisme. Sensibilisée et supervisée à la pratique de l’ABA pendant 3 années, j’ai ensuite été formée pendant 3 ans et demi à la méthode SACCADE*. Spécialiste de l’autisme, je mets en avant mes compétences de psychologue (test psychologique, entretien parental, analyse du fonctionnement de la personne autiste, restitution sous forme de bilan…). J’essayerai de vous apporter soutien et écoute tout au long de notre alliance. »
          </div>
        </div>

        <div class="temoignage-ctn jeanne">
          <div class="say">
            <div class="job-ctn">
              <div class="dot" />
              <span class="job"><span class="first-name">Jeanne</span>, Éducatrice spécialisée</span>
            </div>
            « Je suis éducatrice spécialisée depuis 7 ans, j’ai tout de suite été attirée par le milieu de l’autisme. Je me suis d’abord formée à la méthode ABA pendant 2 ans et ai été supervisée tout au long par une psychologue ABA- BCBA. J’ai ensuite été formée à la méthode SACCADE* pendant 3 ans et demi. J’ai pu créer de nombreux supports afin d’apporter dans ma pratique une technicité propre à la complexité de l’autisme, alliant connaissance du terrain et analyse neurocognitive. Je tenterai alors de vous accompagner au mieux dans tout le suivi de prise en charge de votre enfant.»
          </div>
          <div class="wave">
            'wavewavew'
          </div>
          <ToySVG />
        </div>
      </div>

      <div class="next">
        <p>Suite à notre collaboration de 5 années, nous avons décidé de continuer l’aventure ensemble car c’est dans la complémentarité de nos métiers et de nos connaissances qu’il nous a semblé avoir les meilleurs résultats. Le cabinet Autism & Advice met un point d'honneur à suivre les recommandations de l' <a target="_blank" href="https://www.has-sante.fr/">HAS</a>.</p>
      </div>

      <div class="precision">
        <p>*: Le cabinet Autism&Advice ne pratique aucune formation, ni supervision concernant la méthode saccade. Seul l’organisme <a href="https://saccade.ca/" target="_blank">Saccade.ca</a> est habilité à former et à superviser leurs méthodes.</p>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'AutictoHero',

  methods: {
    goToAuticto () {
      this.$router.push('/auticto')
    }
  }
}
</script>

<style lang="scss" scoped>
section {
  background-image: radial-gradient( circle farthest-corner at 10% 20%,  rgba(234,249,249,0.67) 0.1%, rgba(239,249,251,0.63) 90.1% );
  min-height: 100vh;

  .hero {
    margin: 0 auto;
    width: 80%;
    max-width: 1200px;
    padding: 60px 0;

    .ctnr {
      background: rgb(255, 255, 255);
      box-shadow: 0px 2px 7px rgba(139, 139, 139, 0.2);
      padding: 40px;
      box-sizing: border-box;
      border-radius: 8px;
      margin-top: 50px;
    }

    .temoignage-ctn {
      display: flex;
      align-items: center;
      margin: 0 auto;

      svg {
        width: 100%;
        max-width: 230px;
        min-width: 155px;
      }

      .wave {
        text-decoration: underline;
        text-decoration-color: rgb(46, 217, 166);
        text-decoration-style: wavy;
        color: transparent;
        height: 10px;
        margin: 0px 0 70px;
        font-size: 30px;
      }

      .inner-ctn {
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
      }

      .say {
        line-height: 1.7;
        text-align: justify;
        font-size: 0.9em;

        .job {
          font-style: italic;
          display: inline-block;

          .first-name {
            font-weight: bold;
          }
        }
      }

    }

    .evelyn {

      .say {
        margin-left: 25px;
      }

      .inner-ctn {
        margin-right: 20px;
      }
    }

    .jeanne {
      margin-top: 30px;

      .say {
        margin-right: 25px;
      }

      .inner-ctn {
        margin-left: 20px;
      }
    }

    @media screen and (max-width: 768px) {

      .ctnr {
        padding: 20px;
      }

      .evelyn {
        flex-direction: column;

        .say {
          margin-left: 0;
        }
      }

      .jeanne {
        flex-direction: column;

        .say {
          margin-right: 0;
        }
      }
    }

    h1 {
      font-size: 32px;
      font-weight: 600;
      color: #162a48;
      margin-bottom: 15px;
      padding: 30px 0 2px;
      font-weight: 700;
      width: fit-content;
      border-bottom: 3px solid rgb(46, 217, 166);
    }

    h4 {
      font-size: 24px;
      font-weight: 400;
      line-height: 1.4;
      color: #646668;
      margin: 0 auto 30px;
    }

    p {
      text-align: initial;
    }

    p, a, .say {
      color: #646668;
    }

    .say {
      margin-top: 25px;

      .job-ctn {
        margin-bottom: 15px;
      }

      @media screen and (max-width: 768px) {
        .job-ctn {
          display: flex;
          align-items: center;
          border-bottom: 1px solid rgb(46, 217, 166);
          padding-bottom: 0px;
          width: fit-content;
        }

        .dot {
          border-radius: 50%;
          background: rgb(46, 217, 166);
          width: 10px;
          height: 10px;
          margin-right: 10px;
        }

      }

    }

    .next {
      font-size: 1.1em;
      margin-top: 50px;
      line-height: 1.5;
    }

    .precision {
      font-size: 0.8em;
      margin-top: 50px;
    }

    .auticto-word {
          position: relative;
          cursor: pointer;
          padding-bottom: 3px;
          font-weight: 700;
          background: -webkit-linear-gradient(rgb(46, 217, 166), rgb(46, 189, 217));
          font-size: 1.5rem;
          -webkit-background-clip: text;
          -webkit-text-fill-color: transparent;

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

    .auticto {
        display: flex;

        button {
          font-size: 1.2em;
          font-family: 'Ubuntu', sans-serif;
          border: none;
          background: rgb(46, 217, 166);
          color: white;
          padding: 10px 20px;
          border-radius: 2px;
          cursor: pointer;
          align-self: center;
          box-shadow: 0px 2px 7px rgba(139, 139, 139, 0.3);

          &:hover {
            filter: brightness(1.1);
          }
        }
      }
  }

  @media screen and (max-width: 768px) {
    h1 {
      font-size: 1.9em !important;
    }

    h4 {
      font-size: 1.3em !important;
      display: inline-block;
      margin: 15px auto 10px auto !important;
    }
  }

  @media screen and (max-width: 700px) {
    .hero {
      padding-bottom: 100px;
    }
  }

}

.wave {
  display: none;
}

@media screen and (max-width: 768px) {
  .wave {
    display: block;
  }
}
</style>
