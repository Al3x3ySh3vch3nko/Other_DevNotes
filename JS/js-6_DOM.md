********
## DOM - API ���������, ������� ��������� ������ JS ����������������� � html
********
***
__����� ���������. �������� DOM ��������� ����� �������__
***
`console.log(document.documentElement)` // ���
`console.log(document.head)` // ������� head
`console.log(document.body)` // ������� body

��������� ������ ����� ��� getElementByTagName \ ByClassName ���������� �� ������������ \ node list, � life collection. �� ����, ��������� ���������, ������� ������������� �����������

* ��� ������� ��������� ����� ���������.
`document;`   

* ����� ������� ��������� ��������
`document.firstElementChild;`

* ����� ������� ��������� ��� ������� ���������.
`document.firstElementChild.document.firstElementChild`

* ����� ���������� ��������� ��������.
`document.lastElementChild`

* ���������� ���������� ���������� �������� � ����������
(������)
`var heading = document.firstElementChild.document.firstElementChild`
� ����������� ��
`heading.innerHTML = "Good Bye";`
`heading.style.color = "red";`

* ����� ���� ����(�������)
`document.querySelector("input").click();`

* ����� �� ���� ����
`document.getElementsByTagName("li");`
������ ���������� ��������� ��� ��������� � ����
`document.getElementByTagName("li").style.color ="purple";`
������, ��� ��� ����������� ��������� � ������. ��� ������ ����������� �������� ����� ��������� ����� � �������:
`document.getElementByTagName("li")[2].style.color ="purple";`
`const allButtons = document.getElementByTagName (button)`
`console.log(allButtons` // ������� ��� �������� � ����� button

* ����� �� ������
`document.getElementsByClassName("btn");`
�� ���������:
`document.getElementsByClassName("btn").style.color = "red";`
�����
`document.getElementsByClassName("btn")[0].style.color = "red";`

* ����� �� ID
`document.getElementById("btn");`
c��������, ��� ��� ��� �� ������, � ��������� ������:
`document.getElementById("btn").innerHTML = "Good Bye";`

* ����� �� ��������� ������ �������, ���������������� ����������.
`document.querySelector("h1");`
`document.querySelector("#title");`
`document.querySelector(".btn");`

* ����������:
`document.querySelector("li a");`
`document.querySelector("li.title");` (���� ����� � ���� ��� ��������)
`document.querySelector("li .title");` (���� ����� � ���� ��� ����� ������� �������)

* ����� �� ��������� ���� ��������, ��������������� ����������.
`document.querySelectorAll("li a");` 
* ����������� ���������� �� �������.
`document.querySelectorAll("li a")[2].style.color = "blue";`
***
__����������� DOM__
***
`const h1 = document.querySelector('h1')`;
����� �������� h1

* Going downwards: child
`console.log(h1.querySelectorAll('.highlight'));` // ����� ���� ��������� � ������� � �������� h1
`console.log(h1.childNodes);` // ������ ���-���������
`console.log(h1.children);` // ������ �������� ��������� (�� �������� ��� ���-��������) - ���� html ���������
`h1.firstElementChild.style.color = 'white';` // ������ �������� �������
`h1.lastElementChild.style.color = 'orangered';` // ��������� �������� �������

* Going upwards: parents
`console.log(h1.parentNode);` // ����� ������������� ���-��������
`console.log(h1.parentElement);` // ����� ������������� html-��������
`h1.closest('.header').style.background = 'var(--gradient-secondary)';`
`h1.closest('h1').style.background = 'var(--gradient-primary)';`
// �����, ���������� ������������ ������� ���������� �� ��� ��������� � DOM

* Going sideways: siblings
`console.log(h1.previousElementSibling);`
`console.log(h1.nextElementSibling);`
`console.log(h1.previousSibling);`
`console.log(h1.nextSibling);`
```
console.log(h1.parentElement.children);
[...h1.parentElement.children].forEach(function (el) {
  if (el !== h1) el.style.transform = 'scale(0.5)';
});
```

* ������ ���� ����������� � ������� ������� (� �������)
`.classList;`
������:
`document.querySelector("button").classList;`

* �������� ����� � �����:
`document.querySelector("button").classList.add("invisible");`

* ������������ ����� � �����:
`document.querySelector("button").className = 'form-control error'`

* ������� ����� �� �����:
`document.querySelector("button").classList.remove("invisible");`

* �������������:
`document.querySelector("button").classList.toggle("invisible");`

* ������ ������:
� ���������� ������:
`document.getElementById("title").innerHTML = "Good Bye";`
������ �����:
`document.getElementById("title").textContent = "Good Bye";`
    
* ����� �� ���������:
`document.querySelector("a");`
�����
`document.querySelector("a").attributes;`
����� ������ ��������� � ����� ������� ����������� �������:
`document.querySelector("a").getAttribute("href");`
���������� ����� �������:
`document.querySelector("a").setAttribute("href", "http:....");`

***
__����������� � ����������__
***
__�������� ���������__ 
* �� ����� insertAdjacentHTML (������� � bankist app)
* document.createElement('div')

������ ���������� ����� � ����������� � cookie
`const header = document.querySelector('.header')`
// ����� �������� � ������� ����� ������������ ���������
`const cookiesMessage = document.createElement('div')`
// �������� ������ div ��� ����� �������� ���������
`cookiesMessage.classList.add('cookie-message')`
// ���������� � ����� ������ div ������ �� ������� �� css
`message.innerHTML = 'We use cookies for improve functionality and analytics. '<button class="btn btn--close-cookie"> Ok! </button>'`
// ���������� ������ � �������� � div
`header.prepend('message')`
���
`header.append('message')`
// ����� ������� ��� ������ ��������� cookies. ����� prepend ��������� ������� ��� ������ �������� �������, append - ��� ��������� 

��� ���������� ����� �������� 
`header.prepend('message')`
`header.append('message.cloneNode(true)')`

* ��������� �������� �� \ ����� 
`header.before('message')`
`header.after('message')`

* �������� ���������
`document.qerySelector('.btn--close-cookie')`
`addEventListener('click', function()`
`{`
    `message.remove()`
`})`

__���������� ������ � ���������__
`message.style.backgroundColor = '#37383d'`
`message.style.width = '120%'`
\\ ������ message ����� ������������ ��������� �������

������ ����� ��������� �������� ������ � ������, ������� ������ ������

��� �� ��������� ��������� ������������ ����� 
`getComputedStyle(message).color` \\ ������ color - ����������� ��������

����� �������� �������� � ������������� ����� js
`message.style.height = Number.parseFloat(getComputedStyle(message).height, 10) + 40 + 'px'`

* ��� ��������� ������ �� css: root (� js ��� ���������� document)
`document.documentElement.style.setProperty('--color-primary', 'oranged')`
\\ �������� �������� --color-primary �� :root �ss �� �����

* ��� ��������� ������� � ��������� (����������� ��������)
`const logo = document.querySelector('.nav__logo')`
`console.log(logo.alt)`
`console.log(logo.src)` \\ ���� �������� ���� - ����������
`console.getAttribute('src')` \\ ���� ���� ��� �� ��� �������� � ���� - ����� ���� ������������� 

`console.log(logo.className)`

��� ��������� ������� � ������������� ��������� 
`logo.getAttribute('designer')`
��� ������������ ��������
`logo.getAttribute('company', 'bankist')` \\ ������ �������� ��� �������� ��������, ������ - ��� ��������

��� ���������� ��������
`logo.alt('��� ����')` \\ ������ alt ��������� ��������� ������ ������� 

��� ��������� ��������� � ��������� 'data-' (������: <img data-version-number = '3.0') ��������� ������������ ��������� �����

`console.log(logo.dataset.versionNumber)`

__ ������ ������ � ��������__
`logo.classList.add('�����1', '�����2')`
`logo.classList.remove('�����1', '�����2')`
`logo.classList.toggle('�����1', '�����2')`
`logo.classList.contains('�����1', '�����2')`

__��������� �������� html__
`console.log(document.querySelector('�������������').textContent`
������� html ���������� "�������"

__��������� �������� �� input__
��� ��������� � ������������ �������� �� ���� input ��� � ���� input ��������� ������������ value

������:
��������� - `console.log(document.querySelector('������������� ���� input').value)`
���������� �������� - `document.querySelector('������������� ���� input').value = ��������` `document.querySelector('�������������').addEventListener('��� ������', �������-handler)`

***
#### EventsListener:
***

__Event__ - ��� ������, ������� ������������ �� ����������� DOM ���� ��� �����-�� ������� � ���� �����. ������ ����� �������������� ������ ��������������� ���� ���� ��� EventsListener �� ����.
__� �������� ����� �������� ������ 1 ��������, � ��� - �����. ��� �������� ������ ����� ������������ this ��� ���������� �� ����� ������ ��� ������__
`event.target` - �������, �� ������� ���������� �������� �����
`event.currentTarget` - �������, �� ������� ����������� ����� � ��������� ������ (�� �� ����� ��� � this � ����������)

������:
__1) capturing__ - ��� ������� event "������" ������������ � document � ������� ����� ������������ �������� ��������, � ����� � ������� ��������� �������, �� � ����� ��������

__2) targeting__ - ��� ������� ������� ������ ����� ������� �������-������

__3) bubbling__ - ��� ������������ ��������� event ����� ������������ �������� ������������ ������� � ������ document

__C������ �������� eventListener__ 
__1.__ ����� ����� (��������� ��������� ��������� ���������� � ������ ��������, ��������� ������ �������� ���� �� ����� �� �����)
```
const h1 = document.querySelector('h1')
h1.addEventListener('mouseenter', function(event) 
{
    alert ('hello')
}
```
__2.__ ����� ������ (��� ���������� ������� ��������� � �������� �� ��������� ������, �� ��������� ������ �������� ���� �� ����� �� �����)
```
h1.onmouseenter = function(event) 
{
    alert ('hello')
}
```
__3.__ � �������� HTML (�� ������������)
`<h1 onclick = 'alert' ('HTML alert')>`
__4.__ �������� eventListener ����� ������������� (�������� ���������� �� �������� 1 ��������� ������������� �������� �������� ��������� - ������ ������ ��� ��� ��������� ������ �������� �� ������������ ��� (� ������� ��������) ���������)

__������ ������__
- ���������� ��������� � �������� ������������� �������� 
- ���������� �� ����� �������� ������ ��������� eventListener (����� event.target)

__�������� ��������� (������ ��� ������� � 1)__
```
const h1 = document.querySelector('h1')
const alertH1 = function(event) 
{
    alert ('hello')
    h1.removeEventListener('mouseenter', alertH1)
}

h1.addEventListener('mouseenter', alertH1)
```
������� ����� ��������� �����
```
setTimeout(() =>h1.removeEventListener('mouseenter', alertH1), 3000)
```

__�������� bubbling ��� capturing__

`event.stopPropagation()`
 
_� ������ ���������� ���� �������� �� ����������� ����� ������������ ��������� ���_ 

`if (!guess) {���}`

� ������ ������ ���� �������� �������� - � ������ ������ ���������� guess ����� ���� �� ��������������� �������� falses (0 ��� ���������� ��������)
������:
```
if (!guess)
{
    document.querySelector(.message).textContent = 'No Number'
}
```
������:
C������� ������� �� ����� �� ��� ������ � ������� drum (7 ����)
```
    let drumNumber = document.querySelectorAll('.drum').length;

for (i=0; i<drumNumber; i++)
{
    document.querySelectorAll('.drum')[i].addEventListener('click', f_listenerClick)
}

function f_listenerClick()
{
    alert('@#$')
}
```

��� ������������ ������� ������ ������� ������� "����������" EventsListener
```
document.addEventListener('keydown', function(event)
{
    console.log(event)
})
```

��� ������������ ������ : 
```
console.log(event.key)
```
��� ������������ �� ������� ������:
```
document.addEventListener('keydown', function(event)
{
    if(event.key === 'Escape')
    {
        
    }
})
```
��� ����, ����� ���������� ����� ����� � ������ ������ ��������/ �� �������� ��������
```
document.addEventListener('keydown', function(event)
{
    if(event.key === 'Escape')
    {
        if(modal.classList..contains('hidden'))
        {
            
        }
        if(!modal.classList..contains('hidden'))
        {
            
        }
    }
})
```
��� 
```
document.addEventListener('keydown', function(event)
{
    if(event.key === 'Escape' && !modal.classList.contains('hidden'))
    {
    f_closeModal()
    }
})
```
������ � ������ ��� ���������.
```
//Var1
document.querySelector("button").addEventListener("click", handleClick)
function handleClick()
{
alert("I got clicked");
}
```
```
//Var2
document.querySelector("button").addEventListener("click", function(){alert('I got clicked.');});
```

__���������� ������� ������� ������ ���������� ��� ���������__
```
var numbersOfDrumButtons = document.querySelectorAll(".drum").length;
for (var i = 0; i < numbersOfDrumButtons; i++) 
    {
    document.querySelectorAll(".drum")[i].addEventListener("click", function()
        {
        alert("i got clicked");
        });
    }
```

___��� ������ ��������� �������:___

��� ���� �����,
```
$0.addEventListener("click", function()
{
    console.log("I got clicked");
}
); 
```
���
```
$0.addEventListener("click", respondToClick);

function respondToCLick()
{
    console.log("I got clicked");
}
```

__������ ������������:__
```
function add(num1, num2)
{
    return num1 + num2;
}

function subtract(num1, num2)
{
    return num1 - num2;
}

function multiply(num1, num2)
{
    return num1 * num2;
}

function divide(num1, num2)
{
    return num1 / num2;
}

function calculator(num1, num2, operator)
{
    return operator(num1, num2);
}
```
�����:
`calculator(4, 5, ��� �������)`;
