<div class="row flex-spaces tabs">
    <input id="tab1" type="radio" name="tabs" checked>
    <label for="tab1">Tab 1</label>
  
    <input id="tab2" type="radio" name="tabs">
    <label for="tab2">Tab 2</label>
  
    <input id="tab3" type="radio" name="tabs">
    <label for="tab3">Tab 3</label>
  
    <input id="tab4" type="radio" name="tabs">
    <label for="tab4">Tab 4</label>
  
    <div class="content" id="content1">
      <p>
        Я публикуюсь в журналах, я молодец
        Bacon ipsum dolor sit amet beef venison beef ribs kielbasa...
      </p>
      <p>
        Brisket meatball turkey short loin boudin leberkas meatloaf...
      </p>
    </div>
    <div class="content" id="content2">
      <p>
        Bacon ipsum dolor sit amet landjaeger sausage brisket...
      </p>
    </div>
    <div class="content" id="content3">
      <p>
        Bacon ipsum dolor sit amet beef venison beef ribs kielbasa...
      </p>
      <p>
        Brisket meatball turkey short loin boudin leberkas meatloaf...
      </p>
    </div>
    <div class="content" id="content4">
      <p>
        Bacon ipsum dolor sit amet landjaeger sausage brisket...
      </p>
    </div>
  </div>

<p> Публикации в журналах: </p>
<br>
<div class="magazine">
    
    <div id="pages" > 

    </div>
    <img class="pages" src="pages.png">

</div>

<img src="ph1.png">

<img src="ph4.png">

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
}

#pages{
    background-color: rgb(147, 147, 147);
    margin-top: 3px;
    margin-bottom: 3px;
}

.pages{
    height: 436px;
    border: 0;
}

.tabs{
    margin-top: 60px;
}

</style>