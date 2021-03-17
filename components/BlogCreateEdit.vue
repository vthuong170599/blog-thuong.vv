<template>
  <div>
    <div class="col-md-8">
      <form action="">
        <div class="form-group">
          <label for="title">Tiêu đề</label>
          <input
            type="text"
            class="form-control"
            name=""
            id="title"
            aria-describedby="helpId"
            placeholder="Tiêu đề"
          />
        </div>
        <div class="form-group">
          <label for="desc">Mô tả ngắn</label>
          <input
            type="text"
            class="form-control"
            name=""
            id="desc"
            aria-describedby="helpId"
            placeholder="Mô tả ngắn"
          />
        </div>
        <div class="form-group">
          <label for="detail">chi tiết</label>
          <textarea
            class="form-control"
            name=""
            id="detail"
            rows="6"
            placeholder="chi tiết"
          ></textarea>
        </div>
        <div class="form-group">
          <label for="desc">Hình ảnh</label>
          <input
            type="file"
            class="form-control"
            name=""
            id="desc"
            aria-describedby="helpId"
            placeholder="Mô tả ngắn"
          />
        </div>
        <div class="form-group">
          <label for="species">loại</label>
          <select class="form-control" name="" id="species">
            <option>Thời sự</option>
            <option></option>
            <option></option>
          </select>
        </div>
        <label for="">Vị trí</label>
        <div class="form-check">
          <label class="form-check-label">
            <input
              type="radio"
              class="form-check-input"
              name=""
              id=""
              value="checkedValue"
              checked
            />
            Việt Nam </label
          ><br />
          <label class="form-check-label">
            <input
              type="radio"
              class="form-check-input"
              name=""
              id=""
              value="checkedValue"
            />
            Châu Á </label
          ><br />
          <label class="form-check-label">
            <input
              type="radio"
              class="form-check-input"
              name=""
              id=""
              value="checkedValue"
            />
            Châu Âu </label
          ><br />
          <label class="form-check-label">
            <input
              type="radio"
              class="form-check-input"
              name=""
              id=""
              value="checkedValue"
            />
            Châu Mỹ
          </label>
        </div>
        <label for="" class="mt-2">Public</label>
        <div class="form-check">
          <label class="form-check-label">
            <input
              type="radio"
              class="form-check-input"
              name=""
              id=""
              value="checkedValue"
              checked
            />
            yes </label
          ><br />
          <label class="form-check-label">
            <input
              type="radio"
              class="form-check-input"
              name=""
              id=""
              value="checkedValue"
            />
            No
          </label>
        </div>
        <div class="form-group mt-3">
          <label for="desc">Date public</label>
          <input
            style="width: 30%"
            type="date"
            class="form-control"
            name=""
            id="desc"
            aria-describedby="helpId"
            placeholder="Mô tả ngắn"
          />
        </div>
        <div style="margin-left: 45%; margin-bottom: 10%">
          <button type="submit" class="btn btn-success">Submit</button>
          <button type="button" class="btn btn-primary">Clear</button>
        </div>
      </form>
    </div>
  </div>
</template>
<script>
export default {
    name: 'blog-create-edit'
}
</script>
<style scoped>

</style>