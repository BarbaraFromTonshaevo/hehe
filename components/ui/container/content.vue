<template>
  <div
    ref="contentBody"
    class="content-container"
  >
    <slot />
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const contentBody = ref(null)
onMounted(() => {
  // добавление внешней обертки для таблиц
  contentBody.value.querySelectorAll('table').forEach((table) => {
    const wrapper = document.createElement('div')
    wrapper.classList.add('table-wrap')

    table.parentNode.insertBefore(wrapper, table)
    wrapper.appendChild(table)
  })
})
</script>

<style lang="scss">
.align-left {
  margin: 38px 40px 38px 0;
  float: left;
}

.align-right {
  margin: 30px 0 30px 40px;
  float: right;
}

.content-container {
  color: var(--text-default);
  line-height: 1.3;
  h1,
  h2,
  h3,
  h4,
  h5,
  h6 {
    font-family: var(--font-title);
    font-style: normal;
    font-weight: 400;
    color: var(--text-prim);
  }

  h1,
  h2 {
    margin-bottom: 40px;
  }

  h3,
  h4,
  h5,
  h6 {
    margin-bottom: 24px;
  }

  h1 {
    font-size: 78px;
    line-height: 100%;
  }

  h2 {
    font-size: 44px;
    line-height: 115%;
  }

  h3 {
    font-size: 32px;
    line-height: 110%;
  }

  h4 {
    font-size: 24px;
    line-height: 115%;
  }

  h5 {
    font-size: 20px;
    line-height: 110%;
  }

  * + h1,
  * + h2 {
    margin-top: 60px;
  }

  p + p,
  * + p,
  * + ul,
  * + ol,
  * + table,
  * + .table-wrap,
  * + picture,
  * + img,
  * + iframe,
  * + h3,
  * + h4,
  * + h5,
  * + h6 {
    margin-top: 24px;
  }

  ol,
  ul {
    display: flex;
    flex-direction: column;
    gap: 12px;
  }

  ol {
    counter-reset: num;
  }
  ol li {
    counter-increment: num;

    &::before {
      content: counter(num) ")";
      margin-right: 10px;
      color: var(--marker);
    }
  }

  ul li {
    position: relative;
    padding-left: 18px;

    &::before {
      content: "";
      position: absolute;
      left: 0;
      top: 7px;
      width: 8px;
      aspect-ratio: 1;
      background-color: var(--marker);
      border-radius: 50%;
    }
  }

  * + table {
    margin-top: 60px;
  }

  table {
    width: 100%;
    border-spacing: 0;
    border-collapse: unset;
    border-radius: 20px;
  }

  th,
  td {
    padding: 24px;
  }

  th {
    font-weight: 700;
    color: var(--text-prim);
    background-color: var(--bg-sec);
    text-align: left;
    border-bottom: 1px solid var(--stroke-card);
    border-top: 1px solid var(--stroke-card);
  }

  th:first-child {
    border-radius: 10px 0 0 10px;
  }

  th:last-child {
    border-radius: 0 10px 10px 0;
  }

  tr td {
    border-bottom: 1px solid var(--stroke-card);
  }

  img {
    max-width: 100%;
    border-radius: var(--br-xs);
  }

  a {
    color: var(--btn-prim);
    text-decoration: underline;
    text-decoration-skip-ink: none;
    text-underline-offset: 1px;
    transition: color 0.3s ease;

    @include hover {
      &:hover {
        color: var(--btn-prim-hover);
      }
    }
  }
}

@include tablet {
  .content-container {
    h1,
    h2,
    h3,
    h4,
    h5,
    h6 {
      hyphens: auto;
    }

    h1 {
      font-size: 38px;
    }

    h2 {
      font-size: 26px;
    }

    h3 {
      font-size: 22px;
    }

    h4 {
      font-size: 20px;
    }

    h5 {
      font-size: 18px;
    }

    h1,
    h2 {
      margin-bottom: 24px;
    }

    * + h1,
    * + h2 {
      margin-top: 40px;
    }

    h3,
    h4,
    h5,
    h6 {
      margin-bottom: 18px;
    }

    p + p,
    * + p,
    * + ul,
    * + ol,
    * + h3,
    * + h4,
    * + h5,
    * + h6,
    * + .table-wrap {
      margin-top: 16px;
    }

    * + img {
      margin: 16px auto 0;
    }

    img {
      float: none;
    }
  }
  .table-wrap {
    overflow-x: auto;
    padding-right: 20px;
    margin-right: -20px;
  }
}
</style>
