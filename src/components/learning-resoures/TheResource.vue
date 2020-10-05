<template>
  <div>
    <base-card>
      <base-button
        @click="setSelectedTab('stored-resources')"
        :mode="storedResourcesBtnMode"
      >
        Stored Resources
      </base-button>
      <base-button
        @click="setSelectedTab('add-resource')"
        :mode="addResourceBtnMode"
      >
        Add Resouce
      </base-button>
    </base-card>
    <keep-alive>
      <component :is="selectedTab"></component>
    </keep-alive>
  </div>
</template>

<script>
import StoredResources from './StoredResources';
import AddResource from './AddResource';

export default {
  components: {
    StoredResources,
    AddResource
  },
  data() {
    return {
      selectedTab: 'stored-resources'
    };
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    }
  },
  provide() {
    return {
      setSelectedTab: this.setSelectedTab
    };
  },
  computed: {
    storedResourcesBtnMode() {
      return this.selectedTab === 'stored-resources' ? null : 'flat';
    },
    addResourceBtnMode() {
      return this.selectedTab === 'add-resource' ? null : 'flat';
    }
  }
};
</script>
