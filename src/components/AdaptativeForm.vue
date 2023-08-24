<template>
    <div id="uform" style="min-height: 100vh; display: flex!important; flex-direction: column; justify-content: center; overflow: hidden;">
      <div class="mb-5"></div>
      <form class="d-flex flex-column justify-content-center align-items-center">

        <!-- CONTAINER 1 -->
        <transition name="slide-fade" mode="out-in">  
          <div v-if="currentContainer === 1" key="container1" class="container d-flex justify-content-center align-items-center flex-column">
            <div style="z-index: 0;">
              <img class="position-absolute start-0 top-0"  src="../assets/circuit.svg" alt="" srcset="">
              <img class="position-absolute start-50 top-0"  src="../assets/circuit2.svg" alt="" srcset="">
              <img class="position-absolute start-0" style="top: -100px;" src="../assets/circuit2.svg" alt="" srcset="">
              <img class="position-absolute top-50" style="right: -870px;;"  src="../assets/circuit3.svg" alt="" srcset="">
              <img class="position-absolute" style="left: -830px; bottom: -170px; transform: rotate(180deg);"  src="../assets/circuit3.svg" alt="" srcset="">
            </div>
              <div class="col-8 p-4" style="z-index: 1;">
                <h2 class="mb-3" style="color: #222">Construisez <span class="title_underline">votre Solution</span></h2>
                <p>Pour commencer, nous aurions besoin d'en savoir un peu plus sur vous</p>
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

          <!-- CONTAINER 2 -->
          <transition name="slide-fade" mode="out-in">
            <div v-if="currentContainer === 2" key="container2" class="w-100 position-absolute top-50 start-50 translate-middle d-flex justify-content-center align-items-center flex-column">
              <div style="z-index: 0; height: 100vh;" class="w-100 position-absolute">
                <img class="position-absolute start-0 top-0"  src="../assets/circuit.svg" alt="" srcset="">
                <img class="position-absolute start-50 top-0"  src="../assets/circuit2.svg" alt="" srcset="">
                <img class="position-absolute start-0" style="top: -100px;" src="../assets/circuit2.svg" alt="" srcset="">
                <img class="position-absolute top-50" style="right: -870px;;"  src="../assets/circuit3.svg" alt="" srcset="">
                <img class="position-absolute" style="left: -830px; bottom: -170px; transform: rotate(180deg);"  src="../assets/circuit3.svg" alt="" srcset="">
            </div>
              <div v-if="isLoading" style="z-index: 1;">
                <div>
                  <h3 style="font-size: 40px; color: #222; font-weight: bold;">Votre solution est <br> en cours de construction</h3>
                </div>
                <div>
                  <img src="../assets/loader.gif" alt="" srcset="">
                </div>
                <!-- <div class="col-5 d-flex justify-content-center align-items-center">
                  <svg class="mx-3" xmlns="http://www.w3.org/2000/svg" width="30" height="30" viewBox="0 0 30 30" fill="none">
                    <mask id="mask0_112_25" style="mask-type:luminance" maskUnits="userSpaceOnUse" x="0" y="0" width="30" height="30">
                      <path d="M15 28C16.7075 28.0022 18.3986 27.6669 19.9761 27.0135C21.5537 26.36 22.9865 25.4013 24.1923 24.1923C25.4013 22.9865 26.36 21.5537 27.0135 19.9761C27.6669 18.3986 28.0022 16.7075 28 15C28.0022 13.2925 27.6669 11.6014 27.0134 10.0239C26.36 8.44636 25.4012 7.01353 24.1923 5.80771C22.9865 4.59873 21.5537 3.63996 19.9761 2.98651C18.3986 2.33305 16.7075 1.9978 15 2.00001C13.2925 1.99783 11.6014 2.3331 10.0239 2.98656C8.44636 3.64001 7.01353 4.59876 5.80771 5.80771C4.59876 7.01353 3.64001 8.44636 2.98656 10.0239C2.3331 11.6014 1.99783 13.2925 2.00001 15C1.9978 16.7075 2.33305 18.3986 2.98651 19.9761C3.63996 21.5537 4.59873 22.9865 5.80771 24.1923C7.01353 25.4012 8.44636 26.36 10.0239 27.0134C11.6014 27.6669 13.2925 28.0022 15 28Z" fill="white" stroke="white" stroke-width="4" stroke-linejoin="round"/>
                      <path d="M9.80005 15L13.7 18.9L21.5 11.1" stroke="black" stroke-width="4" stroke-linecap="round" stroke-linejoin="round"/>
                    </mask>
                    <g mask="url(#mask0_112_25)">
                      <path d="M-0.600098 -0.599976H30.5999V30.6H-0.600098V-0.599976Z" fill="#FFA900"/>
                    </g>
                  </svg>
                  <p style="margin: 0; padding: 0; font-weight: bold;">Assemblage des modules</p>
                  
                </div> -->
              </div>
              <div style="height: 50px;" class="col-12 d-flex justify-content-center align-items-center">
                <div  v-if="showPhrases" class="col-5 d-flex justify-content-center align-items-center">

                  <svg class="mx-3 svg-ico" xmlns="http://www.w3.org/2000/svg" width="30" height="30" viewBox="0 0 30 30" fill="none">
                      <mask id="mask0_112_25" style="mask-type:luminance" maskUnits="userSpaceOnUse" x="0" y="0" width="30" height="30">
                        <path d="M15 28C16.7075 28.0022 18.3986 27.6669 19.9761 27.0135C21.5537 26.36 22.9865 25.4013 24.1923 24.1923C25.4013 22.9865 26.36 21.5537 27.0135 19.9761C27.6669 18.3986 28.0022 16.7075 28 15C28.0022 13.2925 27.6669 11.6014 27.0134 10.0239C26.36 8.44636 25.4012 7.01353 24.1923 5.80771C22.9865 4.59873 21.5537 3.63996 19.9761 2.98651C18.3986 2.33305 16.7075 1.9978 15 2.00001C13.2925 1.99783 11.6014 2.3331 10.0239 2.98656C8.44636 3.64001 7.01353 4.59876 5.80771 5.80771C4.59876 7.01353 3.64001 8.44636 2.98656 10.0239C2.3331 11.6014 1.99783 13.2925 2.00001 15C1.9978 16.7075 2.33305 18.3986 2.98651 19.9761C3.63996 21.5537 4.59873 22.9865 5.80771 24.1923C7.01353 25.4012 8.44636 26.36 10.0239 27.0134C11.6014 27.6669 13.2925 28.0022 15 28Z" fill="white" stroke="white" stroke-width="4" stroke-linejoin="round"/>
                        <path d="M9.80005 15L13.7 18.9L21.5 11.1" stroke="black" stroke-width="4" stroke-linecap="round" stroke-linejoin="round"/>
                      </mask>
                      <g mask="url(#mask0_112_25)">
                        <path d="M-0.600098 -0.599976H30.5999V30.6H-0.600098V-0.599976Z" fill="#FFA900"/>
                      </g>
                  </svg>
                  <p class="phrase" style="margin: 0; padding: 0; font-weight: bold;">{{ currentPhrase }}</p>
                </div>
              </div>
            </div>
          </transition>

          <!-- CONTAINER 3 -->
          <transition name="slide-fade" mode="out-in">
            <div v-if="currentContainer === 3" key="container3" class="w-100 position-absolute top-50 start-50 translate-middle d-flex justify-content-center align-items-center flex-column">
              <div>
                <h3 style="font-size: 40px; color: #222; font-weight: bold;">Votre solution est <br> en cours de construction</h3>
              </div>
              <div class="col-5 d-flex justify-content-center align-items-center">
                <svg class="mx-3" xmlns="http://www.w3.org/2000/svg" width="30" height="30" viewBox="0 0 30 30" fill="none">
                  <mask id="mask0_112_25" style="mask-type:luminance" maskUnits="userSpaceOnUse" x="0" y="0" width="30" height="30">
                    <path d="M15 28C16.7075 28.0022 18.3986 27.6669 19.9761 27.0135C21.5537 26.36 22.9865 25.4013 24.1923 24.1923C25.4013 22.9865 26.36 21.5537 27.0135 19.9761C27.6669 18.3986 28.0022 16.7075 28 15C28.0022 13.2925 27.6669 11.6014 27.0134 10.0239C26.36 8.44636 25.4012 7.01353 24.1923 5.80771C22.9865 4.59873 21.5537 3.63996 19.9761 2.98651C18.3986 2.33305 16.7075 1.9978 15 2.00001C13.2925 1.99783 11.6014 2.3331 10.0239 2.98656C8.44636 3.64001 7.01353 4.59876 5.80771 5.80771C4.59876 7.01353 3.64001 8.44636 2.98656 10.0239C2.3331 11.6014 1.99783 13.2925 2.00001 15C1.9978 16.7075 2.33305 18.3986 2.98651 19.9761C3.63996 21.5537 4.59873 22.9865 5.80771 24.1923C7.01353 25.4012 8.44636 26.36 10.0239 27.0134C11.6014 27.6669 13.2925 28.0022 15 28Z" fill="white" stroke="white" stroke-width="4" stroke-linejoin="round"/>
                    <path d="M9.80005 15L13.7 18.9L21.5 11.1" stroke="black" stroke-width="4" stroke-linecap="round" stroke-linejoin="round"/>
                  </mask>
                  <g mask="url(#mask0_112_25)">
                    <path d="M-0.600098 -0.599976H30.5999V30.6H-0.600098V-0.599976Z" fill="#FFA900"/>
                  </g>
                </svg>
                <p style="margin: 0; padding: 0; font-weight: bold;">aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaAssemblage des modules</p>
              </div>
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
        isLoading: false,
        showPhrases: true,
        currentPhraseIndex: 0,
        currentPhrase: "Assemblage des modules",
        phrases: [
          "Assemblage des modules",
          "Construction de l'interface",
          "Connexion au serveur"
        ],
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
    mounted() {
      this.displayPhrases();
    },
    methods: {
        displayPhrases() {
          setInterval(() => {
            this.showPhrases = false;

            setTimeout(() => {
              this.currentPhraseIndex = (this.currentPhraseIndex + 1) % this.phrases.length;
              this.currentPhrase = this.phrases[this.currentPhraseIndex];
              this.showPhrases = true;
            }, 300); // Durée d'affichage de chaque phrase en millisecondes
          }, 4000); // Délai entre chaque phrase en millisecondes
        },
        transitionToContainer(containerNumber) {
          this.currentContainer = containerNumber;
          if (containerNumber === 2) {
            this.isLoading = true;
            setTimeout(() => {
              this.isLoading = false;
              this.transitionToContainer(3); // Passer au container 3 après 10 secondes
            }, 11000); // Délai de 10 secondes
          }
        },
        resetContainers() {
          this.currentContainer = 1;
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


.fade-up-enter-active, .fade-up-leave-active {
  transition: opacity 1s, transform 1s;
}
.fade-up-enter, .fade-up-leave-to {
  opacity: 0;
  transform: translateY(20px);
}
.phrase {
  margin-bottom: 20px;
  animation: fadeInUp 1s ease-in-out;
  animation-fill-mode: both;
}
.svg-ico{
  animation: fadeInUp 1s ease-in-out;
  animation-fill-mode: both;
}

@keyframes fadeInUp {
  0% {
    opacity: 0;
    transform: translateY(20px);
  }
  100% {
    opacity: 1;
    transform: translateY(0);
  }
}







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
  