<!-- 搜索表单 -->
<template>
  <el-form
    label-width="77px"
    class="ele-form-search"
    @keyup.enter.native="search"
    @submit.native.prevent
  >
    <el-row :gutter="15">
      <el-col :lg="6" :md="12">
        <el-form-item label="文件名称:">
          <el-input clearable v-model="where.name" placeholder="请输入" />
        </el-form-item>
      </el-col>
      <el-col :lg="6" :md="12">
        <el-form-item label="文件路径:">
          <el-input clearable v-model="where.path" placeholder="请输入" />
        </el-form-item>
      </el-col>
      <el-col :lg="6" :md="12">
        <el-form-item label="上传人:">
          <el-input
            clearable
            v-model="where.createNickname"
            placeholder="请输入"
          />
        </el-form-item>
      </el-col>
      <el-col :lg="6" :md="12">
        <div class="ele-form-actions">
          <el-button
            type="primary"
            icon="el-icon-search"
            class="ele-btn-icon"
            @click="search"
          >
            查询
          </el-button>
          <el-button @click="reset">重置</el-button>
        </div>
      </el-col>
    </el-row>
  </el-form>
</template>

<script>
  export default {
    data() {
      // 默认表单数据
      const defaultWhere = {
        name: '',
        path: '',
        createNickname: ''
      };
      return {
        // 表单数据
        where: { ...defaultWhere }
      };
    },
    methods: {
      /* 搜索 */
      search() {
        this.$emit('search', this.where);
      },
      /*  重置 */
      reset() {
        this.where = { ...this.defaultWhere };
        this.search();
      }
    }
  };
</script>
