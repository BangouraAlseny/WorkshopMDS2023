<template>
    <div id="uform">
      <h1>Formulaire TalkMe</h1>
      <form class="d-flex flex-column justify-content-center align-items-center">
        <div class="container d-flex justify-content-center align-items-center flex-column">
            <div>
                <label for="sector">Sélectionnez votre secteur d'activité :</label>
            </div>
            <div class="col-3">
              <select v-model="selectedSector" id="sector" class="form-select col-5">
                <option value="">Choisissez un secteur</option>
                <option v-for="sector in sectors" :key="sector.value" :value="sector.value">{{ sector.label }}</option>
              </select>
            </div>
        </div>
  
        <div v-if="selectedSector" :class="[selectedSector + '-section', 'section']" class="col-10">
          <h2>Questions pour le secteur {{ selectedSector }}</h2>
          <div v-for="(question, index) in getQuestions(selectedSector)" :key="index" v-show="currentQuestion === index">
            <p>{{ question.label }}</p>
            <template v-if="question.type === 'radio'">
                <div class="d-flex justify-content-center flex-wrap">
                    <div v-for="(option, optionIndex) in question.options" :key="optionIndex">
                        <label>
                          <input :type="question.type" :name="'question-' + index" :value="option" v-model="question.answers[selectedSector]" @change="nextQuestion" hidden />
                          <div class="card m-3 justify-content-center align-item-center" style="width: 150px; height: 150px;">{{ option }}</div>
                        </label>
                    </div>
                </div>
            </template>
            <template v-else-if="question.type === 'select'">
              <select v-model="question.answers[selectedSector]" @change="nextQuestion">
                <option value="">Choisissez une réponse</option>
                <option v-for="(option, optionIndex) in question.options" :key="optionIndex" :value="option">{{ option }}</option>
              </select>
            </template>
          </div>
        </div>
  
        <div v-if="remainingQuestions === 0">
          <p>Vous avez répondu à toutes les questions requises.</p>
        </div>
  
        <button @click="submitForm" v-if="remainingQuestions === 0">Prise de contact</button>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        selectedSector: '',
        currentQuestion: 0,
        sectors: [
          { label: 'Agriculture', value: 'agriculture' },
          { label: 'Automobile', value: 'automobile' },
          { label: 'Technologie', value: 'technologie' },
          { label: 'Santé', value: 'sante' },
          { label: 'Mode', value: 'mode' },
          // Ajoutez d'autres secteurs ici
        ],
        questions: {
          agriculture: [
            { label: 'Quel type d\'animal préférez-vous ?', type: 'radio', options: ['Vache', 'Mouton', 'Poulet'], answers: { agriculture: '' } },
            { label: 'Quel est votre fruit préféré ?', type: 'radio', options: ['Pomme', 'Banane', 'Orange'], answers: { agriculture: '' } },
            { label: 'Avez-vous un jardin ?', type: 'radio', options: ['Oui', 'Non'], answers: { agriculture: '' } },
            // Ajoutez d'autres questions pour le secteur agriculture
          ],
          automobile: [
            { label: 'Quelle marque de voiture préférez-vous ?', type: 'radio', options: ['Toyota', 'Ford', 'Honda'], answers: { automobile: '' } },
            { label: 'Préférez-vous les voitures électriques ?', type: 'radio', options: ['Oui', 'Non'], answers: { automobile: '' } },
            { label: 'Quelle est votre couleur de voiture préférée ?', type: 'select', options: ['Rouge', 'Bleu', 'Noir', 'Blanc'], answers: { automobile: '' } },
            // Ajoutez d'autres questions pour le secteur automobile
          ],
          technologie: [
            { label: 'Quel langage de programmation préférez-vous ?', type: 'radio', options: ['JavaScript', 'Python', 'Java', 'C++'], answers: { technologie: '' } },
            { label: 'Utilisez-vous des frameworks JavaScript ?', type: 'radio', options: ['Oui', 'Non'], answers: { technologie: '' } },
            { label: 'Quelle est votre plateforme de développement préférée ?', type: 'radio', options: ['Visual Studio Code', 'IntelliJ IDEA', 'Eclipse'], answers: { technologie: '' } },
            // Ajoutez d'autres questions pour le secteur technologie
          ],
          sante: [
            { label: 'Quelle activité sportive préférez-vous ?', type: 'radio', options: ['Course à pied', 'Natation', 'Yoga', 'Football'], answers: { sante: '' } },
            { label: 'Suivez-vous un régime alimentaire ?', type: 'radio', options: ['Oui', 'Non'], answers: { sante: '' } },
            { label: 'Combien d\'heures de sommeil avez-vous en moyenne par nuit ?', type: 'select', options: ['Moins de 5 heures', '5-7 heures', 'Plus de 7 heures'], answers: { sante: '' } },
            // Ajoutez d'autres questions pour le secteur santé
          ],
          mode: [
            { label: 'Quel style vestimentaire préférez-vous ?', type: 'radio', options: ['Décontracté', 'Classique', 'Sportif'], answers: { mode: '' } },
            { label: 'Préférez-vous les vêtements de marque ?', type: 'radio', options: ['Oui', 'Non'], answers: { mode: '' } },
            { label: 'Quel accessoire de mode ne quittez-vous jamais ?', type: 'radio', options: ['Montre', 'Bijoux', 'Chapeau', 'Sac à main'], answers: { mode: '' } },
            // Ajoutez d'autres questions pour le secteur mode
          ],
          // Ajoutez d'autres secteurs et leurs questions ici
        },
      };
    },
    computed: {
      remainingQuestions() {
        if (this.selectedSector && this.questions[this.selectedSector]) {
          return this.questions[this.selectedSector].filter(question => !question.answers[this.selectedSector]).length;
        }
        return '';
      }
    },
    methods: {
      submitForm() {
        alert('Formulaire soumis avec succès!');
        // ici pour envoyer la requête au serveur etc..
      },
      getQuestions(sector) {
        return this.questions[sector];
      },
      nextQuestion() {
        if (this.currentQuestion < this.questions[this.selectedSector].length - 1) {
          this.currentQuestion++;
        }
      },
    },
  };
  </script>
  
  <style>
  #uform{
    padding-top: 50px;
  }
  .agriculture-section {
    background-color: green;
    color: white;
  }
  
  .automobile-section {
    background-color: gray;
    color: white;
  }
  
  .technologie-section {
    background-color: blue;
    color: white;
  }
  
  .sante-section {
    background-color: orange;
    color: white;
  }
  
  .mode-section {
    background-color: pink;
    color: white;
  }
  
  /* Ajoutez des styles pour d'autres sections ici */
  .section {
    padding: 10px;
    margin-top: 20px;
  }
  
  button:disabled {
    background-color: lightgray;
    cursor: not-allowed;
  }
  </style>
  