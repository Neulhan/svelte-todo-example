<script>
  import { todoList } from "../store";

  let todo = "";

  const addTodo = () => {
    if (todo) {
      const newTodo = {
        pk: $todoList[0] ? $todoList[0].pk + 1 : 1,
        name: todo,
        created: new Date(),
        checked: false,
      };
      $todoList = [newTodo, ...$todoList];
      todo = "";
      return;
    }
    alert("한 글자 이상 입력해야 합니다.");
  };
</script>

<style lang="scss">
  @import "../scss/_definition.scss";
  .input-wrapper {
    @include custom-flex(center, space-between);
    margin-bottom: 16px;
    input {
      width: 82%;
      height: 50px;
      border: 1px solid $gray-100;
      border-radius: 4px;
    }
    button {
      height: 50px;
      width: 13%;
      background-color: $blue;
      color: $gray-0;
      border-radius: 4px;
    }
  }
</style>

<div class="input-wrapper">
  <input type="text" bind:value={todo} placeholder="할 일을 입력해주세요." />
  <button on:click={addTodo}>추가</button>
</div>
