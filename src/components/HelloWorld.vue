<template>
  <div class="hello">
    <button @click="doIt(dbProjects, dirProjects)">Click</button>
    {{ dirPaths }}
    <hr />
    {{ newArr }}
    <p></p>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  methods: {
    doIt(dbProjects, dirProjects) {
      //const students = [{name: 'Rich', score: 33}, {name: 'Peter', score: 55}];
      // Run through array and fetch scores

      this.dirPaths = dirProjects.map(function (dirPath) {
        return dirPath.item_path;
      });

      for (var i = 0; this.dirPaths.length; i++) {
        this.findPath(this.dbProjects, this.dirPaths[i]);
      }
    },
    findPath(dbProjects, dirPath) {
      console.log(dirPath);
      const { length } = dbProjects;
      const id = length + 1;
      const found = dbProjects.some((el) => el.path === dirPath);
      if (found)
        this.newArr.push({
          id1: "2",
          id: this.findId(dbProjects, dirPath),
          projectId: dbProjects.projectId,
          path: dirPath,
        });
    },
    findId(dbProjects, dirPath) {
      dbProjects
        .filter((item) => item.path === dirPath)
        .map((item) => item.projectId);
    },
  },
  data() {
    return {
      newArr: [],
      dirPaths: [],
      dbProjects: [
        { path: "a/b/c", projectId: "1" },
        { path: "d/e/f", projectId: "2" },
      ],
      dirProjects: [
        {
          item_path: "a/b/c",
          item_audio_path: "path/to/audio",
          item_image: "path/to/image",
          item_daw_type: "abelton",
        },
        {
          item_path: "d/e/f",
          item_audio_path: "path/to/audio2",
          item_image: "path/to/image",
          item_daw_type: "abelton",
        },
      ],
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
