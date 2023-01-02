<div class="main">

<p class="article"> 
  Иногда меня печтают в журналах, потому что лучше меня никто не фотографирует. 
  Топовые журналы в слезах просят прислать им хотя бы одну фотографию. 
</p>



<div class="magazine">
    
  <div id="pages" > 

  </div>

  <img class="pages" src="pages.png">

</div>

<p class="article"> 
  Иногда фотографирую красивых людей. 
  Возможно, они не были такими красивыми, до того, как я их сфотографировал 
</p>

<img src="ph1.png">
<img src="ph2.png">
<img src="ph3.png">

</div>

<script lang="ts">

    import { onMount } from "svelte";
    import { PageFlip } from 'page-flip';

    onMount(async () => {

        let htmlParentElement = document.getElementById("pages")

        let setting = {
            width: window.innerWidth-60, // required parameter - base page width
            height: 430,  // required parameter - base page height
            usePortrait: true,
            autoSize: false
        }

        const pageFlip = new PageFlip(htmlParentElement, setting);

        pageFlip.loadFromImages([ 'ph4.png', 'ph5.png', 'ph6.png', 'ph1.png', 'ph2.png', 'ph3.png', 'ph6.png', 'ph5.png' ]);

    });

</script>

<style lang="scss">

.magazine{
    display: flex;
    background-color: rgb(147, 147, 147);
    border: 0;
    border-radius: 5px;
    box-shadow: 1px 1px 15px rgb(0, 0, 0) ;
    margin: 15px;
}

#pages{
    background-color: rgb(147, 147, 147);
    margin-top: 3px;
    margin-bottom: 3px;
}

.pages{
    height: 436px;
    border: 0;
    margin: 0;
}

img{
  width: calc(100% - 20px);
  margin: 10px;
}

.article{
  margin: 20px 10px 20px 10px;
}

.main {
  margin-top: 70px;
}

</style>