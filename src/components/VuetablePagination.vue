<template>
        <div class="{{wrapperClass}}">
            <a @click="loadPage(1)"
                class="btn-nav {{linkClass}} {{isOnFirstPage ? disabledClass : ''}}">
                    <i v-if="icons.first != ''" class="{{icons.first}}"></i>
                    <span v-else>&laquo;</span>
            </a>
            <a @click="loadPage('prev')"
                class="btn-nav {{linkClass}} {{isOnFirstPage ? disabledClass : ''}}">
                    <i v-if="icons.next != ''" class="{{icons.prev}}"></i>
                    <span v-else>&nbsp;&lsaquo;</span>
            </a>
            <a v-if="notEnoughPages" v-for="n in totalPage" @click="loadPage(n+1)"
                class="{{pageClass}} {{isCurrentPage(n+1) ? activeClass : ''}}">
                    {{ n+1 }}
            </a>
           <a v-if="!notEnoughPages" v-for="n in windowSize" @click="loadPage(windowStart+n)"
                class="{{pageClass}} {{isCurrentPage(windowStart+n) ? activeClass : ''}}">
                {{ windowStart+n }}
           </a>
            <a @click="loadPage('next')"
                class="btn-nav {{linkClass}} {{isOnLastPage ? disabledClass : ''}}">
                <i v-if="icons.next != ''" class="{{icons.next}}"></i>
                <span v-else>&rsaquo;&nbsp;</span>
            </a>
            <a @click="loadPage(totalPage)"
                class="btn-nav {{linkClass}} {{isOnLastPage ? disabledClass : ''}}">
                <i v-if="icons.last != ''" class="{{icons.last}}"></i>
                <span v-else>&raquo;</span>
            </a>
        </div>
</template>

<script>
import PaginationMixin from './VuetablePaginationMixin.vue'

export default {
    mixins: [PaginationMixin],
}
</script>