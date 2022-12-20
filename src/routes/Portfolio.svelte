<!--div>
    <img src="ph1.png">
    <img src="ph2.png">
    <img src="ph3.png">
</div-->

<div id="pages">

</div>

<script lang="ts">

    import { onMount } from "svelte";
    import { PageFlip } from 'page-flip';

    onMount(async () => {

        let htmlParentElement = document.getElementById("pages")

        let setting = {
            width: window.innerWidth-50, // required parameter - base page width
            height: 450,  // required parameter - base page height
            showCover: true, 
            mobileScrollSupport: false
        }

        const pageFlip = new PageFlip(htmlParentElement, setting);

        pageFlip.loadFromImages(['ph1.png', 'ph2.png', 'ph3.png' ]);

    });

</script>

<style>

img{
    margin-top: 20px;
}

#pages{
    padding: 0;
}

</style>