**3. constructor 안에서 쓰면 constructor로 새로생성되는 오브젝트를 뜻합니다.** 

자바스크립트에서 오브젝트를 비슷한걸 여러개 만들고 싶을 경우

오브젝트를 복사하는게 아니라 constructor라는걸 만들어서 사용합니다.

쉽게 말하면 constructor는 오브젝트 복사해서 생성해주는 기계입니다. 

기계를 어떻게 만드는지 알아봅시다. 

```
function 기계(){
  this.이름 = 'Kim';
}
```

이게 기계 만드는 법입니다. 

함수 문법을 이용해서 만드신 후, 안에 this. 어쩌구를 추가해주시면 됩니다. 

여기서의 this는 **기계로부터 새로 생성될 오브젝트**들을 의미합니다. 

그럼 this.이름 = 'Kim' 이건 무슨 뜻일까요?

새로생성되는 오브젝트의 이름 key값에 'Kim'이라는 value를 집어넣어주세요

라는 뜻 아닐까요? 

맞습니다. 

▼ 이건 참고로 알아두시면 좋은 기계에서 오브젝트 뽑는 법입니다. 

```
function 기계(){
  this.이름 = 'Kim'
}
var 오브젝트 = new 기계();
```

이렇게 new 키워드를 이용하면 새로운 오브젝트를 꺼낼 수 있습니다. 

그리고 새로운 오브젝트는 {이름 : 'Kim'} 이라는 값을 가지고 있습니다.  (this 라는 키워드 덕분에요)

**4. eventlistener 안에서 쓰면 this는 e.currentTarget이라는 의미입니다.**  

이벤트리스너라는 문법 아시쥬?

```
document.getElementById('버튼').addEventListener('click', function(e){
  console.log(this)
});
```

여기서 this를 소환하면 이것은 바로 e.currentTarget이라는 뜻과 똑같은 의미입니다. 

**e.currentTarget은 지금 이벤트가 동작하는 곳**을 뜻합니다. 

매우 간단히 설명하면 지금 addEventListener 부착된 HTML 요소를 뜻한다고 보시면 됩니다. 

의심되면 **e.currentTarget, this, document.getElementById('버튼')** 이거 세개를 각각 출력해보시면 됩니다. 

이게 this의 마지막 뜻입니다. 

**case 1. 이벤트리스너 안에서 콜백함수를 쓴다면 this는?** 

이런 코드를 쓴다고 가정해봅시다. 

```
document.getElementById('버튼').addEventListener('click', function(e){
  var 어레이 = [1,2,3];
  어레이.forEach(function(){
    console.log(this)
  });
});
```

이벤트리스너 안에서 forEach() 라는 반복문을 사용했습니다. 

forEach() 반복문을 사용할 땐 안에 function(){} 콜백함수를 집어넣어서 사용하게 되어있습니다. 그래서 넣었습니다. 

(*** 콜백함수는 그냥 함수 안에 파라미터역할로 들어가는 함수를 뜻합니다. 그게 다임)**

하지만 솔직히 forEach가 무슨 역할을 하는지는 모르셔도 이건 알 수 있습니다. 

**Q. 위의 코드에서 this를 출력하면 무엇이 나올까요?** 

뭐가 나오냐면

**case 2. 오브젝트 안에서 콜백함수를 쓴다면 this는?** 

이번엔 이런 코드를 쓴다고 가정해봅시다. 

```
var 오브젝트 = {
  이름들 : ['김', '이', '박'];
  함수 : function(){
      오브젝트.이름들.forEach(function(){
        console.log(this)
      });
  }
}
```

오브젝트라는 오브젝트 안에 이름들, 함수라는 자료를 각각 저장했습니다 .

함수라는 자료 안에 forEach 반복문을 돌렸는데,

**Q .그럼 여기 안에서의 this값을 출력하면 뭐가나올까요?** 

뭐가 나오냐면

그래서 this값은 function을 만날 때마다 바뀔 수 있기 때문에

내가 원하는 this를 쓰기 힘든 경우가 있습니다. 

그럴 땐 함수를 arrow function으로 바꿔보시길 바랍니다. 

```
var 오브젝트 = {
  이름들 : ['김', '이', '박'];
  함수 : function(){
      오브젝트.이름들.forEach(() => {
        console.log(this)
      });
  }
}
```

자바스크립트 ES6 문법 중,

function () {} 대신 쓸 수 있는 () => {} 이라는 arrow function 문법이 있습니다. 

똑같이 함수 만드는 문법입니다. 

이걸 쓰시면 함수 내부의 this값을 새로 바꿔주지 않기 때문에 this를 사용하실 때 유용합니다. 

심심하면 사용하시길 바랍니다. (아니면 애초에 this 키워드를 쓰지맙시다)