<template>
    <div class="sketch-container">
        <div id="three-sketch" ref="sketch" style="overflow:hidden;"></div> 
    </div>

    <label for="thefile" class="file"> Choose an audio file
      <input type="file" id="thefile" accept="audio/*" />
    </label>

    <audio id="audio" controls></audio>
    <!-- <div id="out"></div> -->
    
</template>

<!-- <style lang="scss">
@import "./ThreeScene.scss"
</style> -->


<script>
import {play} from './script';

export default {
	data() {
	},
	props: {
	},
	methods: {
	},
	components: {
	},
    mounted() {
        var audio = document.getElementById("audio");
        console.log(play)
        var file = document.getElementById("thefile");
        var fileLabel = document.querySelector("label.file");
        let sceneContainer = document.getElementById('three-sketch')

        document.onload = function(e){
            console.log(e);
            audio.play();
            play(sceneContainer);
        }
        file.onchange = function(){
            fileLabel.classList.add('normal');
            audio.classList.add('active');
            var files = this.files;
            
            audio.src = URL.createObjectURL(files[0]);
            audio.load();
            audio.play();
            play(sceneContainer);
        }
	},
};

</script>