# Vue PhotoSwipe  

![npm](https://img.shields.io/npm/l/express.svg)


PhotoSwipe, PhotoSwipeGallery component for Vuejs base on [PhotoSwipe](http://photoswipe.com/).

## Installation  

### NPM  
``` bash
  npm install --save v-photoswipe  
```

## Usage  

### Template  

``` html
<template>
  <div>
    <div class="paragraph">
      <h3>PhotoSwipe</h3>
      <div>
        <img @click="showPhotoSwipe(0)" src="https://farm4.staticflickr.com/3894/15008518202_c265dfa55f_h.jpg" alt="">
        <img @click="showPhotoSwipe(1)" src="https://farm4.staticflickr.com/3902/14985871946_24f47d4b53_h.jpg" alt="">
      </div>
    </div>
    <div class="paragraph">
      <h3>PhotoSwipe Gallery</h3>
      <div>
        <v-photoswipe-gallery :isOpen="isOpenGallery" :options="optionsGallery" :items="items">
          <img slot-scope="props" :src="props.item.src" alt="picture"/>
        </v-photoswipe-gallery>
      </div>
    </div>
    <v-photoswipe :isOpen="isOpen" :items="items" :options="options" @close="hidePhotoSwipe"></v-photoswipe>
  </div>
</template>  
```

### JS  

``` js
import { PhotoSwipe, PhotoSwipeGallery } from 'v-photoswipe'
export default {
  components: {
    'v-photoswipe': PhotoSwipe,
    'v-photoswipe-gallery': PhotoSwipeGallery
  },
  data () {
    return {
      isOpen: false,
      isOpenGallery: false,
      options: {
        index: 0
      },
      optionsGallery: {},
      items: [
        {
          src: 'https://farm4.staticflickr.com/3894/15008518202_c265dfa55f_h.jpg',
          w: 1600,
          h: 1600,
          title: 'This is dummy caption.'
        }, {
          src: 'https://farm4.staticflickr.com/3902/14985871946_24f47d4b53_h.jpg',
          w: 1600,
          h: 1066,
          title: 'This is dummy caption. It has been placed here solely to demonstrate the look and feel of finished, typeset text.'
        }
      ]
    }
  },
  methods: {
    showPhotoSwipe (index) {
      this.isOpen = true
      this.$set(this.options, 'index', index)
    },
    hidePhotoSwipe () {
      this.isOpen = false
    }
  }
}  
```

## Props

### PhotoSwipe & PhotoSwipeGallery  

| Name                | Type        | Default | Required | Description               |
|---------------------|-------------|---------|----------|---------------------------|
| isOpen              |  Boolean    | false   | true     |                           |
| items               |  Array      | []      | true     | [Document](http://photoswipe.com/documentation/getting-started.html)                           |
| options             |  Object     |  {}     | fasle    | [Document](http://photoswipe.com/documentation/options.html)                                   |
| beforeChange        | Function    |         |          | Photoswipe event listener |
| afterChange         | Function    |         |          | Photoswipe event listener |
| imageLoadComplete   | Function    |         |          | Photoswipe event listener |
| resize              | Function    |         |          | Photoswipe event listener |
| gettingData         | Function    |         |          | Photoswipe event listener |
| mouseUsed           | Function    |         |          | Photoswipe event listener |
| initialZoomIn       | Function    |         |          | Photoswipe event listener |
| initialZoomInEnd    | Function    |         |          | Photoswipe event listener |
| initialZoomOut      | Function    |         |          | Photoswipe event listener |
| initialZoomOutEnd   | Function    |         |          | Photoswipe event listener |
| parseVerticalMargin | Function    |         |          | Photoswipe event listener |
| close               | Function    |         |          | Photoswipe event listener |
| unbindEvents        | Function    |         |          | Photoswipe event listener |
| destroy             | Function    |         |          | Photoswipe event listener |
| updateScrollOffset  | Function    |         |          | Photoswipe event listener |
| preventDragEvent    | Function    |         |          | Photoswipe event listener |
| shareLinkClick      | Function    |         |          | Photoswipe event listener |


## Slot   

### PhotoSwipeGallery    

| Name    | Type      | Default      | Required | Description |
|---------|-----------|--------------|----------|-------------|
| item    | Object    | HTML Img Tag | false    |             |


## Demo  

coming soon...

