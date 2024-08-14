<script>
import ClickComp from './components/ClickComp.vue';
import DynamicList from './components/DynamicList.vue';
import EventTimeComp from './components/EventTimeComp.vue';
import ObjectList from './components/ObjectList.vue';
import PaginList from './components/PaginList.vue';
import PreventComp from './components/PreventComp.vue';
import TableComp from './components/TableComp.vue';

export default {
  components: {
    EventTimeComp,
    PreventComp,
    ClickComp,
    DynamicList,
    TableComp,
    ObjectList,
    PaginList
  }
}
</script>

<template>
  <header>

    <div class="wrapper">
      <EventTimeComp />
      <PreventComp />
      <ClickComp />
      <DynamicList />
      <TableComp />
      <ObjectList />
      <PaginList />
    </div>
  </header>

  <main>
  </main>
</template>
