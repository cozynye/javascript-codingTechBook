tip6. includes()로 존재 여부를 확인하라
====

```javascript
string.indexOf(searchvalue,position)

- indexOf 함수는 문자열에서 특정 문자열(searchvalue)를 찾고, 검색된 문자열이 첫번째로 나타나는 위치 index를 리턴
- searchvalue : 필수값, 찾을 문자열
- position : 기본값은 0, string에서 searvalue를 찾기 시작할 위치
```

```javascript
const sections = ['shipping'];

function displayShipping(sections){
    if(sections.indexOf('shipping')){
        return true;
    }
    return false;
}
```

-> if(0)이 되므로 false값을 반환하게 된다


------
## - includes() 배열 메서드를 이용하면 값이 배열에 존재하는지에 따라 true 또는 false를 반환한다

```javascript
const sections= ['shipping'];

function displayShipping(sections){
    return sections.includes('shipping');
}
```