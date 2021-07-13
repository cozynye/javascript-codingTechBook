tip6. includes()로 존재 여부를 확인하라
====

```javascript
const sections = ['shipping'];

function displayShipping(sections){
    if(sections.indexOf('shipping')){
        return true;
    }
    return false;
}
```