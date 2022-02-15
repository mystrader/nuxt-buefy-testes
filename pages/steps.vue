<template>
  <section class="mt-6">
    <h1 class="title">Dhuo Steps</h1>

    <h2 class="subtitle">Exemplo de dhuo com darkTheme aplicado</h2>

    <b-tabs v-model="activeTab">
      <b-tab-item label="Horizontal">
        <div class="block mt-6">
          <b-field grouped group-multiline>
            <div class="control">
              <b-switch v-model="showSocial"> Show Social step </b-switch>
            </div>
            <div class="control">
              <b-switch v-model="isAnimated"> Animated </b-switch>
            </div>
            <div class="control">
              <b-switch v-model="isRounded"> Rounded </b-switch>
            </div>
            <div class="control">
              <b-switch v-model="isStepsClickable"> Clickable Marker </b-switch>
            </div>
          </b-field>
          <b-field grouped group-multiline>
            <div class="control">
              <b-switch v-model="hasNavigation"> Navigation Buttons </b-switch>
            </div>
            <div class="control">
              <b-switch v-model="customNavigation">
                Custom Navigation
              </b-switch>
            </div>
            <div class="control">
              <b-switch v-model="isProfileSuccess">
                Set <code>is-success</code> for profile
              </b-switch>
            </div>
          </b-field>
          <b-field v-if="hasNavigation" grouped group-multiline>
            <b-field label="Prev icon">
              <b-select v-model="prevIcon">
                <option value="chevron-left">Chevron</option>
                <option value="arrow-left">Arrow</option>
              </b-select>
            </b-field>
            <b-field label="Next icon">
              <b-select v-model="nextIcon">
                <option value="chevron-right">Chevron</option>
                <option value="arrow-right">Arrow</option>
              </b-select>
            </b-field>
            <b-field label="Label position">
              <b-select v-model="labelPosition">
                <option value="bottom">Bottom</option>
                <option value="right">Right</option>
                <option value="left">Left</option>
              </b-select>
            </b-field>
            <b-field label="Mobile mode">
              <b-select v-model="mobileMode">
                <option :value="null">-</option>
                <option value="minimalist">Minimalist</option>
                <option value="compact">Compact</option>
              </b-select>
            </b-field>
          </b-field>
        </div>
        <b-steps
          v-model="activeStep"
          :animated="isAnimated"
          :rounded="isRounded"
          :has-navigation="hasNavigation"
          :icon-prev="prevIcon"
          :icon-next="nextIcon"
          :label-position="labelPosition"
          :mobile-mode="mobileMode"
        >
          <b-step-item step="1" label="Account" :clickable="isStepsClickable">
            <h1 class="title has-text-centered">Account</h1>
            Lorem ipsum dolor sit amet.
          </b-step-item>

          <b-step-item
            step="2"
            label="Profile"
            :clickable="isStepsClickable"
            :type="{ 'is-success': isProfileSuccess }"
          >
            <h1 class="title has-text-centered">Profile</h1>
            Lorem ipsum dolor sit amet.
          </b-step-item>

          <b-step-item
            step="3"
            :visible="showSocial"
            label="Social"
            :clickable="isStepsClickable"
          >
            <h1 class="title has-text-centered">Social</h1>
            Lorem ipsum dolor sit amet.
          </b-step-item>

          <b-step-item
            :step="showSocial ? '4' : '3'"
            label="Finish"
            :clickable="isStepsClickable"
            disabled
          >
            <h1 class="title has-text-centered">Finish</h1>
            Lorem ipsum dolor sit amet.
          </b-step-item>

          <template v-if="customNavigation" #navigation="{ previous, next }">
            <b-button
              outlined
              type="is-danger"
              icon-pack="fas"
              icon-left="backward"
              :disabled="previous.disabled"
              @click.prevent="previous.action"
            >
              Previous
            </b-button>
            <b-button
              outlined
              type="is-success"
              icon-pack="fas"
              icon-right="forward"
              :disabled="next.disabled"
              @click.prevent="next.action"
            >
              Next
            </b-button>
          </template>
        </b-steps>
      </b-tab-item>

      <b-tab-item label="Vertical">
        <section class="mt-6">
          <b-field grouped group-multiline>
            <div class="control">
              <b-switch
                v-model="position"
                true-value="is-right"
                false-value="is-left"
              >
                Right position
              </b-switch>
            </div>
            <b-field label="Size" label-position="on-border">
              <b-select v-model="size" placeholder="Size">
                <option :value="null">Default</option>
                <option value="is-small">Small</option>
                <option value="is-medium">Medium</option>
                <option value="is-large">Large</option>
              </b-select>
            </b-field>
            <b-field label="Label position" label-position="on-border">
              <b-select v-model="labelPosition">
                <option value="bottom">Bottom</option>
                <option value="right">Right</option>
                <option value="left">Left</option>
              </b-select>
            </b-field>
          </b-field>

          <b-steps
            :position="position"
            :label-position="labelPosition"
            :size="size"
            vertical
          >
            <b-step-item label="Account" icon="account-key">
              Account: Lorem ipsum dolor sit amet. <br />
              Account: Lorem ipsum dolor sit amet. <br />
              Account: Lorem ipsum dolor sit amet.
            </b-step-item>

            <b-step-item label="Profile" icon="account">
              Profile: Lorem ipsum dolor sit amet. <br />
              Profile: Lorem ipsum dolor sit amet.? <br />
              Profile: Lorem ipsum dolor sit amet. <br />
              Profile: Lorem ipsum dolor sit amet.
            </b-step-item>

            <b-step-item label="Social" icon="account-plus" disabled>
              Social: Lorem ipsum dolor sit amet. <br />
              Social: Lorem ipsum dolor sit amet. <br />
              Social: Lorem ipsum dolor sit amet. <br />
              Social: Lorem ipsum dolor sit amet. <br />
              Social: Lorem ipsum dolor sit amet.
            </b-step-item>
          </b-steps>
        </section>
      </b-tab-item>
    </b-tabs>
  </section>
</template>

<script>
export default {
  data() {
    return {
      activeStep: 0,

      showSocial: false,
      activeTab: 0,
      isAnimated: true,
      isRounded: true,
      isStepsClickable: false,

      hasNavigation: true,
      customNavigation: false,
      isProfileSuccess: false,

      prevIcon: 'chevron-left',
      nextIcon: 'chevron-right',
      labelPosition: 'bottom',
      mobileMode: 'minimalist',
      position: null,
      size: null,
    }
  },
}
</script>
