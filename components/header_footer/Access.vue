<template>
    <div id="access_panel">
        <button id="open_access" @click="openAccess()"><span class="show-for-sr">Open the Accessibility Panel</span></button>
        <div class="contain_access">
            <form>
                <fieldset>
                    <legend>Accessibility</legend>
                    <div class="form_body">
                        <div class="form_line">
                            <label for="titleFont">Change Title Font</label>
                            <input type="checkbox" id="titleFont"/>
                            <span class="checkmark"></span>
                        </div>

                        <div class="form_line">
                            <label for="dyslexia">Dyslexia</label>
                            <input type="checkbox" id="dyslexia"/>
                            <span class="checkmark"></span>
                        </div>

                        <div class="form_line">
                            <label for="lineHeight">More line height</label>
                            <input type="checkbox" id="lineHeight"/>
                            <span class="checkmark"></span>
                        </div>
                    </div>
                </fieldset>
            </form>
        </div>
    </div>
</template>

<script>
export default {
  components: {
  },
  mounted() {
  },
  methods: {
      openAccess: function() {
          document.getElementById('access_panel').classList.toggle('open');
      }
  }
}
</script>