<template>
  <div class="Haq">
    <h2 class="title">Score HAQ</h2>
    <span class="line"></span>

    <div v-for="(dataQuestion, i) in datasQuestion" :key="i">
      <HaqQuestion
        :index="i"
        :title="dataQuestion.title"
        :question="dataQuestion.question"
        :malusScore="dataQuestion.malusScore"
        @upwardChange="upwardChange"
      ></HaqQuestion>
      <br/>
    </div>

    <div class="result">
      Score final <em>{{ finalScore }}</em
      >.
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import HaqQuestion from "./HaqQuestion.vue";

export default Vue.extend({
  name: "HAQ",
  components: { HaqQuestion },
  data() {
    return {
      finalScore: 0,
      scores: [],
      datasQuestion: [
        { title: "Habillement, soins corporels", question: "Vous habiller, y compris nouer vos lacets et boutonner vos vêtements ?", malusScore: [0,1,2,3], userScore: 0},
        { question: "Vous laver les cheveux ?", malusScore: [0,0.5,1,1.5], userScore: 0},
        { title: "Se lever", question: "Vous lever d'une chaise ?", malusScore: [0,0.3,0.7,1], userScore: 0},
        { question: "Vous mettre au lit et vous lever du lit ?", malusScore: [0,0.3,0.5,0.8], userScore: 0},
        { title: "Les repas", question: "Couper votre viande ?", malusScore: [0,0.2,0.4,0.6], userScore: 0},
        { question: "Porter à votre bouche 1 tasse ou 1 verre bien plein ?", malusScore: [0,0.2,0.3,0.5], userScore: 0},
        { question: "Ouvrir une brique de lait ou de jus de fruit ?", malusScore: [0,0.1,0.3,0.4], userScore: 0},
        { title: "La marche", question: "Marcher en terrain plat à l'extérieur ?", malusScore: [0,0.1,0.3,0.4], userScore: 0},
        { question: "Monter 5 marches ?", malusScore: [0,0.1,0.2,0.3], userScore: 0},
        { title: "Hygiène", question: "Vous laver et vous sécher entièrement ?", malusScore: [0,0.1,0.2,0.3], userScore: 0},
        { question: "Prendre un bain ?", malusScore: [0,0.1,0.2,0.3], userScore: 0},
        { question: "Vous asseoir et vous relever des toilettes", malusScore: [0,0.1,0.2,0.3], userScore: 0},
        { title: "Attraper", question: "Prendre un objet pesant 2,5 kg situé au-dessus de votre tête ?", malusScore: [0,0.1,0.2,0.2], userScore: 0},
        { question: "Vous baisser pour ramasser un vêtement par terre ?", malusScore: [0,0.1,0.1,0.2], userScore: 0},
        { title: "Préhension", question: "Ouvrir une porte de voiture ?", malusScore: [0,0.1,0.1,0.2], userScore: 0},
        { question: "Dévisser le couvercle d'un pot déjà ouvert une fois ?", malusScore: [0,0.1,0.1,0.2], userScore: 0},
        { question: "Ouvrir et fermer un robinet ?", malusScore: [0,0.1,0.1,0.2], userScore: 0},
        { title: "Autres activités", question: "Faire vos courses ?", malusScore: [0,0.1,0.1,0.2], userScore: 0},
        { question: "Monter et descendre de voiture ?", malusScore: [0,0.1,0.1,0.2], userScore: 0},
        { question: "Faire des travaux ménagers tels que passer l'aspirateur ou faire du petit jardinage ?", malusScore: [0,0.1,0.1,0.2], userScore: 0},
      ],
    };
  },
  methods: {
    calcResult() {
      this.finalScore = this.scores.reduce((x1, x2) => (parseFloat(x1) + parseFloat(x2)).toFixed(1));
    },
    upwardChange(e: any) {
      this.scores[e.index] = e.userScore;
      this.calcResult()
    },
  },
  mounted() {},
});
</script>

<style scoped lang="scss">
@import "src/sass/global.scss";
@import "src/sass/global";

.Haq {
}
</style>
