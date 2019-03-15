### preview-img
图片预览插件
##### js
```js
const closeImgPopup = () => {
  const document = window.document
  const mask = document.getElementById('img-popup')
  if (mask) {
    document.body.removeChild(mask)
    window.onscroll = null
  }
}

const previewImg = (imgSrc) => {
  if (!imgSrc) return false
  const document = window.document
  let img = document.createElement('img')
  img.src = imgSrc

  const oldMask = document.getElementById('img-popup')
  oldMask && document.body.removeChild('oldMask')

  let mask = document.createElement('div')
  mask.setAttribute('id', 'img-popup')
  mask.appendChild(img)
  document.body.appendChild(mask)

  window.onscroll = closeImgPopup
  mask.onclick = closeImgPopup
}

window.utils = window.utils || {}
window.utils.previewImg = previewImg
window.utils.closeImgPopup = closeImgPopup
```
##### css
```css
#img-popup{
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  background: rgba(0,0,0,0.4);
  z-index: 9999;
}
#img-popup img {
  max-width: 90%;
  max-height: 90%;
  border: 5px solid rgba(255,255,255,0.5);
 }
```
