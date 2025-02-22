<template lang="pug">
  div
    h2 JavaScript
    h3 Properties
    p.-text This component accepts options to configure its behavior.

    section.chi-table.chi-table__options.-bordered.-my--3
      div
        table.-text(cellpadding='0', cellspacing='0')
          thead
            tr
              th
                div Option
              th
                div Default
              th
                div Description
          tbody
            tr
              td
                div
                  code= 'animated'
              td
                div
                  code= 'true'
              td
                div
                  | Enables animation on modal display and hide, and fade effect in the backdrop.
            tr
              td
                div
                  code= 'target'
              td
                div
                  code= 'null'
              td
                div
                  | Lets the developer refer the target programmatically instead of by data-target attribute.
                  | It accepts Element object and xpath selector string.

    h3 Methods
    section.chi-table.chi-table__methods.-bordered.-my--3
      div
        table.-text(cellpadding='0', cellspacing='0')
          thead
            tr
              th
                div Method
              th
                div Description
              th
                div Returns
          tbody
            tr
              td
                div
                  code= 'hide() => void'
              td
                div
                  | Hides the modal
              td
                div
                  | Type: void
            tr
              td
                div
                  code= 'show() => void'
              td
                div
                  | Shows the modal
              td
                div
                  | Type: void
            tr
              td
                div
                  code= 'toggle() => void'
              td
                div
                  | Toggles active state (show/hide)
              td
                div
                  | Type: void

    h3 Events
    section.chi-table.-bordered.-my--3
      table(cellpadding='0', cellspacing='0')
        thead
          tr
            th
              div Event
            th
              div Description
        tbody
          tr
            td
              div
                code chiModalShow
            td
              div Modal show method has been executed, but the showing animation has not started yet.
          tr
            td
              div
                code chiModalHide
            td
              div Modal hide method has been executed, but the closing animation has not started yet.
          tr
            td
              div
                code chiModalShown
            td
                | Modal has been shown to the user and is fully visible. The animation has completed.
          tr
            td
              div
                code chiModalHidden
            td
              div
                | Modal has been hidden to the user. The animation has completed.

    h3 Preventing memory leaks
    p.-text
      | Modal components have a dispose function to free all resources attached to the element,
      | such as event listeners and object data. You should call this method when you want to remove the component.
    <pre class="language-javascript">
      <code v-highlight="$data.codeMemory1" class="javascript"></code>
    </pre>

    p.-text
      | It is safe to call the <code>modal</code> method more than once,
      | as it will return any previously created modal component associated with the trigger.
    <pre class="language-javascript">
      <code v-highlight="$data.codeMemory2" class="javascript"></code>
    </pre>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component({
  data: () => {
    return {
      codeMemory1: `var elem = document.getElementById('modal-1');
var modal = chi.modal(elem);
// do stuff
modal.dispose();`,
      codeMemory2: `var elem = document.getElementById('modal-1');
var modal = chi.modal(elem);
var elem2 = document.getElementById('modal-1');
var modal2 = chi.modal(elem2);
modal === modal2; // returns true

modal.dispose(); // Only have to do it once.`
    };
  }
})

export default class Properties extends Vue {}
</script>
