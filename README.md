![fish](https://user-images.githubusercontent.com/110226567/213706360-87de7b9a-53ff-42d0-94ed-a0df788f815d.png)

# π Catch the fish!

λ¬Όκ³ κΈ°λ₯Ό μ‘μλΌ! κ²μ π [Demo](https://imjone.github.io/catch-the-fish/)

<br />

## π’ νλ‘μ νΈ κ°μ

μ£Όμ΄μ§ μκ° λ΄μ μ±κ²λ₯Ό νΌν΄ λ¬Όκ³ κΈ°λ₯Ό ν΄λ¦­νλ κ²μμλλ€.<br />
λ°λλΌ μλ°μ€ν¬λ¦½νΈλ‘ κ°λ¨ν κ²μμ λ§λ€μ΄λ³΄λ©΄ μ€λ ₯ ν₯μμ μ λ§ λμμ΄ λ§μ΄ λλ€λ κΈμ λ³΄κ³ ,<br />
λΉλ‘ κΈ°λ₯μ΄ λ§μ§ μλλΌλ λκΉμ§ ν¬κΈ°νμ§ μκ³  ν΅μ¬ κΈ°λ₯ μμ£Όλ‘ κ΅¬νν΄λ³΄μλ λͺ©νλ₯Ό μ‘κ³  μ§ννκ² λμμ΅λλ€.

<br />

## π¨οΈ μ¬μ© κΈ°μ 

<p>
  <img src="https://img.shields.io/badge/HTML-e34f26?style=flat-square&logo=HTML5&logoColor=white" />
  <img src="https://img.shields.io/badge/CSS-1572b6?style=flat-square&logo=CSS3&logoColor=white" />
  <img src="https://img.shields.io/badge/JavaScript-f7df1e?style=flat-square&logo=JavaScript&logoColor=white" />
</p>

<br />

## π μ£Όμ κΈ°λ₯

- λ¨μ μκ°μ μλ €μ£Όλ νμ΄λ¨Έ μλ
- κ²μ μμ μ λ¬Όκ³ κΈ° λ° μ±κ² λλ€ λ°°μΉ
- λ¬Όκ³ κΈ° ν΄λ¦­ μ μμ μ­μ  λ° μΉ΄μ΄νΈ κ°μ
- μ±κ² ν΄λ¦­ νΉμ νμ μμ μ κ²μ μ’λ£
- κ²μ κ²°κ³Όμ λ°λΌ μ μ ν νμμ°½ λΈμΆ
- λ¦¬νλ μ΄ λ²νΌμ ν΅ν΄ κ²μ λ€μ μμ
- λ°°κ²½μ λ° ν¨κ³Όμ μ¬μ

<br />

## π» μμ€ μ½λ

μ μ²΄ μ½λ λ³΄λ¬ κ°κΈ° π [Notion](https://imjone.notion.site/Catch-the-fish-0f2e6609e83d43e2838d933a9c9c5b39)

### π μ΄λ―Έμ§ λλ€ λ°°μΉ

`Field` ν΄λμ€μ λ©€λ² λ©μλμΈ `createItem()` ν¨μλ₯Ό ν΅ν΄ μ΄λ―Έμ§λ₯Ό λλ€ν μμΉμ λ°°μΉν©λλ€.<br />
μΈμλ‘ μ λ¬ λ°μ λ¬Όκ³ κΈ°μ μ±κ²μ κ°μ λ§νΌ λ°λ³΅λ¬Έμ λλ©° `img` μμλ₯Ό λμ μΌλ‘ μμ±νλ©°,<br />
κ²μ νλμ λ²μλ₯Ό λ²μ΄λμ§ μλλ‘ `randomPosition()` ν¨μλ₯Ό ν΅ν΄ μ΅λ λ²μλ₯Ό μ§μ ν΄μ€λλ€.<br />
μ§μ λ λ²μλ κ°κ° `x`, `y` λ³μμ ν λΉλλ©°, μ΄λ κ³§ μμ±λ μ΄λ―Έμ§λ€μ μ€νμ κ°μ΄ λ©λλ€.

```javascript
export default class Field {
  constructor(fishCount, urchinCount) {
    this.fishCount = fishCount;
    this.urchinCount = urchinCount;
    this.field = document.querySelector('.game__field');
    this.fieldRect = this.field.getBoundingClientRect();
  }

  init() {
    this.field.innerHTML = '';
    this.createItem('fish', this.fishCount, 'img/fish.png');
    this.createItem('urchin', this.urchinCount, 'img/urchin.png');
  }
  // μ΄λ―Έμ§λ₯Ό λμ μΌλ‘ μμ±νμ¬ λλ€ λ°°μΉν΄μ£Όλ ν¨μ
  createItem(className, count, imgSrc) {
    const minX = 0;
    const minY = 0;
    const maxX = this.fieldRect.width - carrotSize;
    const maxY = this.fieldRect.height - carrotSize;
		// μμ΄νλ€μ μμΉκ° μμ­μ λ²μ΄λμ§ μλλ‘

    for (let i = 0; i < count; i++) {
      const item = document.createElement('img');
      item.setAttribute('class', className); // λ§€κ°λ³μλ‘ μ λ¬ν className
      item.setAttribute('src', imgSrc);
      item.style.position = 'absolute';

      const x = randomPosition(minX, maxX);
      const y = randomPosition(minY, maxY);
      item.style.left = `${x}px`;
      item.style.top = `${y}px`;
      this.field.appendChild(item);
    }
  }

// μμ΄νλ€μ λλ€μΌλ‘ λ°°μΉμν¬ μμ­μ μ΅μ, μ΅λ λ²μ μ§μ 
function randomPosition(min, max) {
  return Math.random() * (max - min) + min;
}
```

### π κ²μ κ²°κ³Ό νμμ°½

`Popup` ν΄λμ€μμ νμμ°½κ³Ό κ΄λ ¨λ λͺ¨λ  λ©μλλ₯Ό λλ¦½μ μΌλ‘ κ΄λ¦¬ν©λλ€.<br />
`show()` - μΈμλ‘ μ λ¬ λ°μ λ©μμ§μ ν¨κ» νμμ°½μ νλ©΄μ λ λλ§ν©λλ€.<br />
`hide()` - νμμ°½μ DOM Treeμμ λ€μ μ κ±°ν©λλ€.

```javascript
export default class Popup {
  constructor() {
    this.popup = document.querySelector('.popup');
    this.popupMsg = document.querySelector('.popup__msg');
    this.popupReplay = document.querySelector('.popup__replay');
    this.popupReplay.addEventListener('click', () => {
      this.onClick && this.onClick(); // onClickμ΄ μμ λλ§ νΈμΆ
      hide();
    });
  }

  setClickListener(onClick) {
    this.onClick = onClick; // μΈμλ‘ μ λ¬ λ°μ κ°μ λ©€λ² λ³μμ ν λΉ
  }
  show(msg) {
    this.popupMsg.innerText = msg;
    this.popup.classList.remove('hide');
  }
  hide() {
    this.popup.classList.add('hide');
  }
}
```

## π λ°°μ΄ μ  λ° λλ μ 

- μλ°μ€ν¬λ¦½νΈμ λ€μν APIλ€μ μ¬μ©ν΄λ³΄κ³ , λ¦¬ν©ν λ§μ ν΅ν΄ λͺ¨λνμ μ₯μ κ³Ό μ€μμ±μ λν΄ μκ² λμμ΅λλ€.
- λμμΈ ν¨ν΄μ΄λ λ°μ΄ν° νμμ λ³΄μ₯νλ λ°©λ² λ± μ‘°κΈ λ κΈ°μ μ μΈ λΆλΆμ λν΄ ν° νμ μ΅ν μ μμ΄μ μ’μμ΅λλ€.
- ν΄λμ€ λ¬Έλ²μ μμ§ μ΅μνμ§ μμ μ½λλ₯Ό λ§€λλ½κ² μμ±νκΈ°κ° μ΄λ €μ μ΅λλ€. λ λ§μ κ³΅λΆμ μ°μ΅μ΄ νμν  κ² κ°μ΅λλ€.
