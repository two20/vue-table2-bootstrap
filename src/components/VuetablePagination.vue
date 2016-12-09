<template>
  <ul v-if="tablePagination && tablePagination.last_page > 1" :class="['pagination',wrapperClass]">
    <li :class="[isOnFirstPage ? css.disabledClass : '']">
      <a @click="loadPage(1)">
          <i v-if="icons.first != ''" :class="[icons.first]"></i>
          <span v-else>&laquo;</span>
      </a>
    </li>
    <li :class="[isOnFirstPage ? css.disabledClass : '']">
      <a @click="loadPage('prev')">
          <i v-if="icons.next != ''" :class="[icons.prev]"></i>
          <span v-else>&nbsp;&lsaquo;</span>
      </a>
    </li>
    <template v-if="notEnoughPages">
      <template v-for="n in totalPage">
        <li :class="[isCurrentPage(n) ? css.activeClass : '']">
            <a @click="loadPage(n)" v-html="n"></a>
        </li>
      </template>
    </template>
    <template v-else>
      <template v-for="n in windowSize">
        <li :class="[isCurrentPage(windowStart+n-1) ? css.activeClass : '']">
            <a @click="loadPage(windowStart+n-1)" v-html="windowStart+n-1">
            </a>
        </li>
      </template>
    </template>
    <li :class="[isOnLastPage ? css.disabledClass : '']">
        <a @click="loadPage('next')">
            <i v-if="icons.next != ''" :class="[icons.next]"></i>
            <span v-else>&rsaquo;&nbsp;</span>
        </a>
    </li>
    <li :class="[isOnLastPage ? css.disabledClass : '']">
        <a @click="loadPage(totalPage)">
            <i v-if="icons.last != ''" :class="[icons.last]"></i>
            <span v-else>&raquo;</span>
        </a>
    </li>
  </ul>
</template>

<script>
import PaginationMixin from './VuetablePaginationMixin.vue'

export default {
  mixins: [PaginationMixin],
}
</script>
