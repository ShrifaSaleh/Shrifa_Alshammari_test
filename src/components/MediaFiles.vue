<template>
  <div class="media-files">
    <h4>Media <span class="text">(36)</span></h4>
    <div class="media-grid ">
      <img v-for="(img, index) in media" :key="index" :src="img" alt="Media" />
    </div>
    <h4>Files <span class="text">(36)</span></h4>
    <div class="files">
      <div v-for="(file, index) in files" :key="index" class="file">
        <img :src="file.file" alt="file" />
        <div class="file-info mb-2">
          <p class="file-name">{{ file.name }}</p>
          <p class="file-meta">{{ file.size }} {{ file.date }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      media: [
        require('@/assets/img1.svg'),
        require('@/assets/img2.svg'),
        require('@/assets/img3.svg'),
        require('@/assets/img4.svg'),
        require('@/assets/img5.svg'),
        require('@/assets/img6.svg')
      ],
      files: [
        { name: 'service-task.pdf', file:require('@/assets/file1.svg'), date: '2 Dec 2022', size: '2 MB' },
        { name: 'homepage-design.fig', file:require('@/assets/file2.svg'),  date: '2 Dec 2022', size: '2 MB' },
        { name: 'about-us.html', file:require('@/assets/file3.svg'),  date: '2 Dec 2022', size: '2 MB' },
        { name: 'work-project.zip',file:require('@/assets/file4.svg'),  date: '2 Dec 2022', size: '2 MB' },
        { name: 'custom.js',file:require('@/assets/file5.svg'),  date: '2 Dec 2022', size: '2 MB' }
      ]
    };
  }};
</script>

<style scoped>
.media-files {
  padding: 10px;
  background: #fff;
  max-width: 250px;
  height: 100%; 
}

.media-grid {
  display: grid;
  row-gap: 5px;
  gap: 5px;
  grid-template-columns: auto auto auto;
  padding: 5%; 
  margin: 0px 10px;
}

.media-grid img {
  width: 55px; 
  height: 55px;
  object-fit: cover;
  border-radius: 4px;
}

.files {
  margin-top: 10px;
  margin-left: 28px;
}

.file {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 4px 0; 
}

.file-info {
  display: flex;
  flex-direction: column;
  font-size: 10px; 
}

.file-name {
  font-weight:500;
  margin: 0; 
}

.file-meta {
  color: #98A4AE; 
  font-size: 9px;
  margin: 0; 
}

h4 {
  font-size: 12px;
  color: #333;
  margin-bottom: 6px; 
  margin-left: 28px;
}

.file img{
  margin-bottom: 0px;
  width: 25px;
  height: 25px;
}

span{
  color: #98A4AE;
}
</style>