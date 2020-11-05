<script>
  import { todoList } from "../store";
  export let todo;

  const remove = () => {
    $todoList = $todoList.filter((t) => t.pk !== todo.pk);
  };

  const toggleCheck = () => {
    todo.checked = !todo.checked;
  };
</script>

<style lang="scss">
  @import "../scss/_definition.scss";
  .todo {
    padding: 8px;
    background-color: white;
    border: 1px solid $gray-100;
    color: $gray-800;
    @include custom-flex(center, flex-start);
    border-radius: 4px;
    &.done {
      background-color: $gray-100;
    }
    &:not(:last-child) {
      margin-bottom: 12px;
    }
    .check {
      width: 24px;
      height: 24px;
      background-color: white;
      border: 1px solid $gray-100;
      margin-right: 12px;
      cursor: pointer;
      @include custom-flex(center, center);

      .checked-box {
        background-color: $gray-400;
        width: 12px;
        height: 12px;
      }
    }
    .info {
      .name {
        font-size: 18px;

        &.done {
          color: $gray-400;
          text-decoration: line-through;
        }
      }
      .created {
        color: $gray-400;
        font-size: 14px;
      }
    }

    .delete-button {
      display: none;
    }
    &:hover {
      background-color: $gray-0;
      .delete-button {
        display: block;
        background-color: $red;
        color: $gray-0;
        margin: 0 8px 0 auto;
        align-self: center;
      }
    }
  }
</style>

<div class="todo" class:done={todo.checked}>
  <div class="check" on:click={toggleCheck}>
    {#if todo.checked}
      <div class="checked-box" />
    {/if}
  </div>
  <div class="info">
    <div class="name" class:done={todo.checked}>{todo.name}</div>
    <div class="created">
      {`${todo.created.getFullYear()}년 ${todo.created.getMonth() + 1}월 ${todo.created.getDate()}일 ${todo.created.getHours()}시 ${todo.created.getMinutes()}분 ${todo.created.getSeconds()}초`}
    </div>
  </div>
  <button on:click={remove} class="delete-button">삭제</button>
</div>
