<script>
  import Input from "./Input.svelte";
  import TODO from "./TODO.svelte";
  import { todoList } from "../store";
</script>

<style lang="scss">
  @import "../scss/_definition.scss";
  .container {
    width: 100%;
    min-height: 100%;
    @include custom-flex(flex-start, center);
    background-color: $gray-200;
    .wrapper {
      width: 600px;
      height: 100vh;
      overflow-y: auto;
      padding: 24px;
      background-color: white;
      border: 1px solid $gray-100;

      &::-webkit-scrollbar {
        display: none;
      }
      .no-todo {
        color: $gray-400;
        text-align: center;
        margin-top: 100px;
      }
    }
  }
</style>

<div class="container">
  <div class="wrapper">
    <Input />
    {#each $todoList as todo}
      <TODO {todo} />
    {/each}
    {#if !$todoList.length}
      <div class="no-todo">아직 등록된 TODO가 존재하지 않습니다.</div>
    {/if}
  </div>
</div>
