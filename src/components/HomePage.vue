<template>
  <div class="container">
    <h1>QLDT</h1>
    <form action="" @submit.prevent="addPhone">
      <label for="ten">Tên</label>
      <input type="text" name="ten" class="form-control" v-model="newPhone.Ten" />
      <label for="hang">Hãng</label>
      <select type="text" name="hang" class="form-select" v-model="newPhone.Hang">
        <option value="Samsung">Samsung</option>
        <option value="Apple">Apple</option>
        <option value="Oppo">Oppo</option>
      </select>
      <label for="dungluong">Dung lượng</label>
      <select type="text" name="dung luong" class="form-select" v-model="newPhone.DungLuong">
        <option value="64GB">64GB</option>
        <option value="128GB">128GB</option>
        <option value="256GB">256GB</option>
        <option value="512GB">512GB</option>
        <option value="1TB">1TB</option>
      </select>
      <label for="gia">Gia</label>
      <input
        type="number"
        name="gia"
        class="form-control"
        v-model="newPhone.Gia"
        min="100"
        step="1"
      />
      <button class="btn btn-primary">Add</button>
    </form>
    <br />
    <TablePhone :phones="phones" @event="handleChiTiet" @delete-event="handleDelete" />
  </div>
</template>
<script setup>
import { reactive } from 'vue'
import TablePhone from './TablePhone.vue'
import { initPhones } from '@/data/initPhones'
let phones = reactive(initPhones)
const newPhone = reactive({
  Id: phones.length + 1,
  Ten: '',
  Hang: '',
  DungLuong: '',
  Gia: 0,
})
const addPhone = () => {
  phones.push({
    ...newPhone,
  })
  ;(newPhone.Id = phones[phones.length - 1].Id + 1),
    (newPhone.Ten = ''),
    (newPhone.Hang = ''),
    (newPhone.DungLuong = ''),
    (newPhone.Gia = 0)
}
const handleChiTiet = (item) => {
  ;(newPhone.Id = item.Id),
    (newPhone.Ten = item.Ten),
    (newPhone.Hang = item.Hang),
    (newPhone.DungLuong = item.DungLuong),
    (newPhone.Gia = item.Gia)
}

const handleDelete = (item) => {
  const index = phones.findIndex((i) => i.Id === item.Id)
  if (index !== -1) {
    phones.splice(index, 1) // Xóa phần tử khỏi mảng
  }
  newPhone.Ten = ''
  newPhone.Hang = ''
  newPhone.DungLuong = ''
  newPhone.Gia = 0
}
</script>
