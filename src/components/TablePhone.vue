<template>
  <table class="table table-bordered table-striped">
    <thead>
      <th>ID</th>
      <th>Ten</th>
      <th>Hãng</th>
      <th>Dung Lượng</th>
      <th>Giá</th>
      <th>Act</th>
    </thead>
    <tbody>
      <tr :key="phone.Id" v-for="phone in phones">
        <td>{{ phone.Id }}</td>
        <td>{{ phone.Ten }}</td>
        <td>{{ phone.Hang }}</td>
        <td>{{ phone.Gia }}</td>
        <td>{{ phone.DungLuong }}</td>
        <td>
          <button class="btn btn-info" @click="handleChiTiet(phone)">Chi tiết</button>
          <button class="btn btn-danger" @click="handleDelete(phone)">Xóa</button>
        </td>
      </tr>
    </tbody>
  </table>
</template>
<script setup>
defineProps({
  phones: Array,
})
const emit = defineEmits()
const handleChiTiet = (item) => {
  emit('event', item)
}
const handleDelete = (item) => {
  emit('delete-event', item)
}
</script>
