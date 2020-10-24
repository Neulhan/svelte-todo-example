<script>
  import { todoList } from "../store";
  export let todo;

  const remove = () => {
    $todoList = $todoList.filter((t) => t.pk !== todo.pk);
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
    }
    .name {
      font-size: 18px;
    }
    .created {
      color: $gray-400;
      font-size: 14px;
    }
  }
</style>

<div class="todo">
  <div class="check" on:click={remove} />
  <div class="info">
    <div class="name">{todo.name}</div>
    <div class="created">
      {`${todo.created.getFullYear()}년 ${todo.created.getMonth() + 1}월 ${todo.created.getDate()}일 ${todo.created.getHours()}시 ${todo.created.getMinutes()}분 ${todo.created.getSeconds()}초`}
    </div>
  </div>
</div>
