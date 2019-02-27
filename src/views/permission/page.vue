<template>
  <div class="app-container">
    <div style="display: flex;flex-direction: row;justify-content: space-between">
      <switch-roles @change="handleRolesChange"/>
      <el-tree :data="data" :props="defaultProps" @node-click="handleNodeClick"></el-tree>
    </div>
  </div>
</template>

<script>
  import SwitchRoles from './components/SwitchRoles'

  export default {
    name: 'pagePermission',
    data() {
      return {
        data: [{
          label: '一级 1',
          children: [{
            label: '二级 1-1',
            children: [{
              label: '三级 1-1-1'
            }]
          }]
        }, {
          label: '一级 2',
          children: [{
            label: '二级 2-1',
            children: [{
              label: '三级 2-1-1'
            }]
          }, {
            label: '二级 2-2',
            children: [{
              label: '三级 2-2-1'
            }]
          }]
        }, {
          label: '一级 3',
          children: [{
            label: '二级 3-1',
            children: [{
              label: '三级 3-1-1'
            }]
          }, {
            label: '二级 3-2',
            children: [{
              label: '三级 3-2-1'
            }]
          }]
        }],
        defaultProps: {
          children: 'children',
          label: 'label'
        }
      };
    },
    components: {SwitchRoles},
    methods: {
      handleRolesChange() {
        this.$router.push({path: '/permission/index?' + +new Date()})
      },
      handleNodeClick(data) {
        console.log(data);
      }
    }
  }
</script>
