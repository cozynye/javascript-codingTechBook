tip11. Object.assign()으로 조작 없이 객체를 생성하라
========

객체가 완전하지 않음 - 객체에 기존 데이터가 있는 상태에서 새로운 필드 추가나 외부 api에서 데이터를 가져와 현재 데이터 모델에 연결해야 할 경우
<br>-> 원래의 데이터를 유지하면서 새로운 객체를 생성하기 위해 Object.assign()을 사용할 수 있다



```javascript
간략계산법

AND(&&) expr1 && expr2
expr1을 true로 변환할 수 있는 경우 expr2를 반환, 그렇지 않으면 expr1을 반환

OR(||) expr1 || expr2
expr1을 true로 변환할 수 있으면 expr1을 반환, 그렇지 않으면 expr2를 반환

JS에서는 null, undefined, '', 0 -> false 한값으로 취급
```

```javascript
Object.assign(target, ...sources)
             대상객체,   하나 이상의 출처 객체

- 반환값 -> 대상 객체
- 동일한 키가 존재할 경우 대상 객체의 속성은 출처 객체의 속성으로 덮여짐
- 동일한 속성은 출처 객체 순서 뒤에 위치한 객체에 의해 덮어쓰임
```

```javascript
<script>
    const sports={
        arrow:'gold',
        taekwondo:''

    };

    const news={
        jodo:'bronze',
        taekwondo:'gold'

    };

    const total=Object.assign(sports, news);

    console.log(total);
    console.log(sports);
</script>
```



```javascript
const defaults={
    author:'',
    title:'',
    year:2017,
    rating:null,
}

const book={
    author: 'Joe'
    title: 'Javascript'
}

function addBookDefaults(book,defaults){
    const fields = Object.keys(defaults);
    const update= {};
    for(let i =0; i<fileds.length; i++){
        const field=fields[i];
        updated[field]= book[field] || defaults[field];
    }
    return updated;
}

Object.assign(defaults, book); -> 문제점 : 원본 객체를 조작하게 된다
```

- Object.assign()의 첫번째 인자에 빈 객체를 사용하면 위의 문제를 피할 수 있다

```javascript
const defaults={
    author:'',
    title:'',
    year:2017,
    rating:null,
}

const book={
    author: 'Joe'
    title: 'Javascript'
}


Object.assign({}, defaults, book); 
```

- 현재까지의 방법으로 속성을 복사하면 값만 복사한다
<br>-> 중첩된 객체가 있는 경우는 불가능하다

```javascript
const defaultEmployee = {
    name:{
        fisrt:'',
        last:'',
    },
    years:0,
};
const employee = Object.assign({}, defaultEmployee);

defaultEmployee.name.last='false';
console.log(employee);
console.log(defaultEmployee==employee)
console.log(defaultEmployee.name.last==employee.name.last)

* name에 할당된 객체에 대한 참조만 복사
```

- 중첩된 객체로 인한 문제를 피하는 방법은 두가지
1. 중첩된 객체를 두지 않는 것(객체를 중첩하지 않아도 될 때)
1. Object.assing()을 이용해 중첩된 객체를 복사

```javascript
const defaultEmployee = {
    name:{
        fisrt:'',
        last:'',
    },
    years:0,
};
const employee = Object.assign(
    {}, 
    defaultEmployee,
    {
        name : Object.assign({}, defaultEmployee.name),
    },
);
```

--참조
https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object/assign