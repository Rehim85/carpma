<script>
    let tabloVisibility = "visible"
    $: questionsVisibility = tabloVisibility == "hidden" ? "visible" : "hidden"
    let cevap;
    let rnd1= Math.round(Math.random() * 10);
    let rnd2= Math.round(Math.random() * 10);
    function yeniSoru(){
        rnd1= Math.round(Math.random() * 10);
        rnd2= Math.round(Math.random() * 10);
    }

    let gtVisibility = "hidden";
    let rcVisibility = "hidden";
    let correct = false;

</script>

<main class="main-container" >
    <img style="visibility: {tabloVisibility};" src="carpim-tablosu-ezberleme.jpg" alt="çarpım tablosu" height="696" width="1090" >
    <button on:click={()=>tabloVisibility = "hidden"} style="height: 75px; width: 100px; visibility: {tabloVisibility}" >Sorulara Geç</button>
    <div class="mid-container" style="visibility: {questionsVisibility};">
        <h1>
            {rnd1} X {rnd2} = 
            <input bind:value={cevap}  style="height: 100%;"  type="number" name="" id="">
            <button type="submit" on:click={()=>{if(cevap === (rnd1 * rnd2)){gtVisibility = "visible"; rcVisibility = "hidden"; correct=true}else{rcVisibility = "visible"; gtVisibility = "hidden"; correct = false}}} >Kontrol Et</button>
        </h1>
        <img style="visibility: {gtVisibility};" src="green_tick.png" alt="" height="30px" width="30px">
        <img style="visibility: {rcVisibility};" src="red_cross.png" alt="" height="30px" width="30px">
        <button on:click={()=>{yeniSoru(); correct=false; gtVisibility="hidden"; rcVisibility="hidden"; cevap = {};}} style="visibility: {correct === false ? "hidden" : "visible"};" >Bir sonraki soru</button>
    </div>
</main>

<style>

    :global(body) {     
    margin: 0;
    padding: 0; 
}

.main-container {
    height: 100vh;
    width: 100%;
    align-items: center;
    justify-content: center;
    display: flex;
}
.mid-container {
    height: 100%;
    width: 100%;
    align-items: center;
    justify-content: center;
    display: flex;
    flex-direction: column;
    position: fixed;
}

</style>