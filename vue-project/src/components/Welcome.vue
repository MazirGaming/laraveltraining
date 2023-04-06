<template>
  <h3>Component con nhận Slot</h3>
  <slot>
    <!-- Trong này sẽ nhận tất cả slot truyền vào từ Comp cha mà không có name -->
    <p>Tôi sẽ được xuất hiện mặc định nếu không có slot nào được truyền từ Comp cha</p>
    <p>Nếu có thì sẽ thay thế tất cả nội dung trong thẻ slot</p>
  </slot>
  <slot name="footer">

  </slot>
</template>