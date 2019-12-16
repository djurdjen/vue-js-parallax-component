A component creating a parallax effect on an image within a container

# Install

`npm install --save-dev vue-js-parallax-component`

## Usage

```javascript
import VueParallax from "vue-js-parallax-component";

export default {
  components: { VueParallax }
};
```

```html
<vue-parallax image="https://via.placeholder.com/1280x400.png">
  <span>Optional content</span>
</vue-parallax>
```

### Properties

| Property  | Type                | default | Description                                        |
| --------- | ------------------- | ------- | -------------------------------------------------- |
| image     | `string` (Required) |         | The image used for the parallax effect             |
| intensity | `number`            | 15      | Intensity of the parallax effect ( 20 is highest ) |
