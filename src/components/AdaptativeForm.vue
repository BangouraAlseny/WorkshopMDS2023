<template>
    <div id="uform" style="min-height: 100vh;">
      <div class="mb-5"></div>
      <form class="d-flex flex-column justify-content-center align-items-center">
        <transition name="slide-fade" mode="out-in">  
          <div v-if="currentContainer === 1" key="container1" class="container d-flex justify-content-center align-items-center flex-column">
              <div class="col-8 p-4 shadow rounded-4" style="background: #fff; border-bottom: solid orange 4px;">
                <h2 class="mb-3" style="color: #222">Personnalisez <span class="title_underline">votre Solution</span></h2>
                    <!-- formulaire -->
                    <div class="d-flex flex-column justify-content-center align-items-center col-12">
                      <div class="form-floating mb-3 col-5">
                        <input type="text" class="form-control" id="floatingCompany" placeholder="Nom de l'entreprise">
                        <label for="floatingCompany"><i class="fa fa-home px-2"></i>Nom de l'entreprise</label>
                      </div>
                      <div class="form-floating mb-3 col-5">
                        <input type="text" class="form-control" id="floatingPoste" placeholder="Poste occupé">
                        <label for="floatingPoste"><i class="fa fa-user px-2"></i>Poste occupé</label>
                      </div>
                      <div class="form-floating mb-3 col-5">
                        <input type="email" class="form-control" id="floatingInput" placeholder="adresse.mail@example.com">
                        <label for="floatingInput"><i class="fa fa-envelope px-2"></i>Adresse mail</label>
                      </div>
                      <div class="d-flex">
                          <label class="switch mx-2"><input type="checkbox" />    <div></div>
                          </label>
                          <p>J'accepte recevoir des mails de mise à jours</p>
                      </div>
                      <div class="d-flex flex-column justify-items-around align-content-center mt-4" style="width: 250px;">
                        <button @click="transitionToContainer(2)" class="btn btn-success mb-3">Continuer</button>
                        <a @click="transitionToContainer(2)" class="text-muted">Passer l'étape</a>
                      </div>
                    </div>
                  </div>
                  <!-- <div class="col-10">
                    <div :class="[selectedSector + '-section', 'section']">
                        <h3 class="mb-4">Sélectionnez votre secteur d'activité</h3>
                        
                        <div class="d-flex justify-content-around">
                            <label v-for="sector in sectors" :key="sector.value">
                                <input type="checkbox" :id="sector.value" class="card-checkbox" :value="sector.value" v-model="selectedSectors" hidden>
                                <div class="card-checkbox">
                                  {{ sector.label }}
                                </div>
                            </label>
                        </div>

                        <div v-for="(question, index) in getQuestions(selectedSectors)" :key="index" v-show="currentQuestion === index">
                            <p>{{ question.label }}</p>
                        </div>
                    </div>
                </div> -->
            </div>
          </transition>
          <transition name="slide-fade" mode="out-in">
            <div v-if="currentContainer === 2" key="container2" class="w-100 position-absolute top-50 start-50 translate-middle">
                <img src="../assets/loader_tm.gif" alt="" srcset="">
            </div>
          </transition>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        selectedSector: '',
        currentQuestion: 0,
        currentContainer: 1,
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
      transitionToContainer(containerNumber) {
        this.currentContainer = containerNumber;
      },
      resetContainers() {
        this.currentContainer = 1;
      },
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











/* variables */
:root{
  --color-underline: orange;
  --custom-ease-out: cubic-bezier(0.165, 0.84, 0.44, 1);
}

/* transitions */
/* slide-fade */
.slide-fade-enter-active {
  transition: all 3.0s ease-out;
}

.slide-fade-leave-active {
  transition: all .5s cubic-bezier(1, 0.5, 0.8, 1);
}

.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateY(1000px);
  opacity: 0;
}

  #uform{
    padding-top: 50px;
  }
  .title_underline{
    position: relative;
  }
.title_underline::after {
		content: "";
    position: absolute;
    bottom: -0.01em;
    left: 0;
    width: 100%;
    height: 0px;
    background-repeat: no-repeat;
    background: var(--color-underline);
    transition: all .3s ease;
	}
	
	.title_underline:hover::after {
    transition: all .3s ease;
    height: 4px;
  }

  div.card-checkbox{
    position: relative;
    cursor: pointer;
    margin: 3px;
    padding: 10px;
    width: 150px;
    border: solid rgba(107, 81, 235, 0.212) 2px;
    border-radius: 10px;
    transition: all .5s ease-out;
  }
  div.card-checkbox:hover{
    background: #71757a17;
    outline: solid orange 2px;
    outline-offset: -1px;
    transition: all .2s ease-out;
  }
  input.card-checkbox:checked + div.card-checkbox:hover{
    outline: solid orange 2px;
    outline-offset: 2px;
  }

  input.card-checkbox:checked + div.card-checkbox{
    border-radius: 10px;
    color: white;
    background: orange;
    transition: all .2s ease-out;
  }
  input.card-checkbox:checked + div.card-checkbox::after{
    content: '';
    position: absolute;
    right: 0;
    top: 0;
    width: 15px;
    height: 15px;
    border-radius: 50px;
    border: solid white 2px;
    margin: 2px;
    background:rgb(0, 200, 0);
    
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

/* switch btn */
.switch input {
  position: absolute;
  opacity: 0;
}

/**
 * 1. Adjust this to size
 */

.switch {
  display: inline-block;
  font-size: 20px; /* 1 */
  height: 1em;
  width: 2em;
  background: #ece8d599;
  box-shadow: inset #2222222a 0 0 10px 2px;
  border-radius: 1em;
}

.switch div {
  height: 1em;
  width: 1em;
  border-radius: 1em;
  border: solid #e6e4e46f 2px;
  background: #f11b1b;
  box-shadow: 0 0.1em 0.3em rgba(0,0,0,0.3);
  -webkit-transition: all 300ms;
     -moz-transition: all 300ms;
          transition: all 300ms;
}

.switch input:checked + div {
  -webkit-transform: translate3d(100%, 0, 0);
     -moz-transform: translate3d(100%, 0, 0);
          transform: translate3d(100%, 0, 0);
  background: green;
}


  </style>
  