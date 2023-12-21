## การใช้ Boostrap ใน Vue

1) สร้างโปรเจ็ค Vue ใหม่

2) ติดตั้ง package ของ bootstrap

```
npm install bootstrap
npm install @popperjs/core
```

3) เพิ่มการเรียกใช้ในไฟล์ src/main.js

```
import 'bootstrap/dist/css/bootstrap.css'
import "bootstrap"
```

4) ทดสอบโดยเพิ่มโค้ด

```
 <div class="container">
     <button type="button" class="btn btn-success">Success</button>
     <button type="button" class="btn btn-info">Info</button>
     <button type="button" class="btn btn-warning">Warning</button>
  </div>
```


![Bootstrap](images/00_01_test_bootstrap.png)

## การใช้  Vuetify ใน Vue

1) สร้างโปรเจ็ค Vue ใหม่

2) ติดตั้ง package ของ Vuetify

```
npm i vuetify
```

3) เพิ่มการเรียกใช้ในไฟล์ src/main.js

```
// Vuetify
import 'vuetify/styles'
import { createVuetify } from 'vuetify'
import * as components from 'vuetify/components'
import * as directives from 'vuetify/directives'

const vuetify = createVuetify({
  components,
  directives,
})

const app = createApp(App)
app.use(vuetify)
app.mount('#app')
```

4) ทดสอบโดยเพิ่มโค้ด
```
<div class="container m-5">
        <h3>Test Vuetify</h3>
        <v-btn color="success" class="m-2">
          Success
        </v-btn>
        <v-btn color="info"  class="m-2">
          Info
        </v-btn>
        <v-btn color="warning"  class="m-2">
          Warning
        </v-btn>
    </div>
```

![Vuetify](images/00_02_test_vuetify.png)

5) การใช้ icon ของ vuetify เพิ่มโค้ดใน src/main.js

```
import { aliases, mdi } from 'vuetify/iconsets/mdi'
import '@mdi/font/css/materialdesignicons.css' 

export default createVuetify({
  icons: {
    defaultSet: 'mdi',
    aliases,
    sets: {
      mdi,
    },
  },
})
```

6) ทดสอบการใช้ icon
```
<v-icon icon="mdi-home" color="primary"/>
```