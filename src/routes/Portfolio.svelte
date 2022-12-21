<!--div>
    <img src="ph1.png">
    <img src="ph2.png">
    <img src="ph3.png">
</div-->

<p>Публикации в журналах:</p>
<br>
<div class="magazine">
    <div id="pages" > 

    </div>
    <img class="pages" src="pages.png">
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

        pageFlip.loadFromImages(['ph4.png', 'ph1.png', 'ph2.png', 'ph3.png' ]);

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

</style>