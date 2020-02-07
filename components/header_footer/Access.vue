<template>
    <div id="access_panel">
        <button><span class="show-for-sr">Open the Accessibility Panel</span></button>
        <form>
            <fieldset>
                <legend>Accessibility</legend>
                <label for="titleFont">Change Title Font</label>
                <input type="checkbox" id="titleFont"/>

                <label for="dyslexia">Dyslexia</label>
                <input type="checkbox" id="dyslexia"/>

                <label for="lineHeight">More line height</label>
                <input type="checkbox" id="lineHeight"/>
            </fieldset>
        </form>
    </div>
</template>

<script>
export default {
  components: {
  }
}
</script>