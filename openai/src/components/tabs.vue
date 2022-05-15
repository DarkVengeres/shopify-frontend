<template>
    <div>
        <ul id="tagContainer">
            <button id= "Q&A" @click="selectCategorie('Q&A')">Q&A</button>
            <button id= "Grammar" @click="selectCategorie('Grammar')">Grammar</button>
            <button id= "Ad Helper" @click="selectCategorie('Ad Helper')">Ad Helper</button>
            <button id= "Analogy Maker" @click="selectCategorie('Analogy Maker')">Analogy Maker</button>
            <button id= "Essay outline" @click="selectCategorie('Essay outline')">Essay outline</button>
            <button id= "Shortcut finder" @click="selectCategorie('Shortcut finder')">Shortcut finder</button>
            
        </ul>
        <transition name="fade" mode="out-in">
            <QandA v-if="activeCategorie =='Q&A'"></QandA>
            <Grammar v-if="activeCategorie =='Grammar'"></Grammar>
            <AdHelper v-if="activeCategorie =='Ad Helper'"></AdHelper>
            <AnalogyMaker v-if="activeCategorie =='Analogy Maker'"></AnalogyMaker>
            <EssayOutline v-if="activeCategorie =='Essay outline'"></EssayOutline>
            <ShortcutFinder v-if="activeCategorie =='Shortcut finder'"></ShortcutFinder>
        </transition>
    </div>
</template>

<script>
import QandA from './../components/categories/QandA.vue';
import Grammar from './../components/categories/Grammar.vue';
import AdHelper from './../components/categories/AdHelper.vue';
import AnalogyMaker from './../components/categories/AnalogyMaker.vue';
import EssayOutline from './../components/categories/EssayOutline.vue';
import ShortcutFinder from './../components/categories/ShortcutFinder.vue';

export default {
    data () {
        return {
            activeCategorie : 'Q&A',
        }
    },
    methods : {
        selectCategorie(categorie) {
            this.activeCategorie = categorie;
            document.getElementById('Q&A').className = "";
            document.getElementById('Grammar').className = "";
            document.getElementById('Ad Helper').className = "";
            document.getElementById('Analogy Maker').className = "";
            document.getElementById('Essay outline').className = "";
            document.getElementById('Shortcut finder').className = "";
            document.getElementById(categorie).className = "active";
        }
    },
    components: {
        QandA,
        Grammar,
        AdHelper,
        AnalogyMaker,
        EssayOutline,
        ShortcutFinder,
    },
    mounted () {
        document.getElementById(this.activeCategorie).className = "active";

    },
}
</script>

<style scoped>

    #tagContainer {
        display: flex;
        flex-wrap: wrap;
        flex-direction: row;
        justify-content: center;
        align-items: center;
        border-radius: 4px;
        width: 100%;
    }

    button {
        width: 130px;
        margin: 10px;
        height: 64px;
        background-color: var(--wave);
        border : 4px solid var(--primary);
        color: var(--primary);
    }

    button:hover {
        transform: translateY(-5px);
        box-shadow: 0px 0px 10px 0px var(--primary);
    }

    button:hover::after{
        content: "";
        position: absolute;
        top: 70px;
        left: 0;
        width: 100%;
        height: 5%;
        background-color: var(--primary);
        opacity: 1;
        border-radius: 5px;
    }
    .active{
        background-color: var(--primary);
        color: var(--textTitles);
        box-shadow: 0px 0px 10px 0px var(--primary);
    }

    .fade-enter-active,
    .fade-leave-active {
        transition: opacity .3s ease-in-out;
    }

    .fade-enter,
    .fade-leave-to {
        opacity: 0;
    }



    
   
</style>


