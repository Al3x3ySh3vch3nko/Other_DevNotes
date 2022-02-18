
=======
���������� �������
=======

\\ smooth scroll


const btnScrollTo = document.querySelector('.btn--scroll-to')
const section1 = document.querySelector('#section--1')

btnScrollTo.addEventListener('click', function (event)
{
        const s1coord = section.getBoundClientRect() 
        \\ ���� ������ � ���������� ��������� ������ � ������ ��������
        
        console.log('current scroll position x\y:', window.pageXOffset, window.pageYOffset) 
        \\ ���� �������� ������� ������� ������ 
    
        console.log('height/width viewport:', 
        document.documentElement.clientHeight,
        document.documentElement.clientWidth) 
        \\���� ������ � ������ �������� �������� 
})

window.scrollTo
({
    left: s1coords.left + window.pageXOffset,
    top: s1coord.top  + window.pageYOffset,
    behaviour: 'smooth'
})

��� ����� ����� ������
������ window.scrollTo

section1.scrollIntoView({behaviour: 'smooth'})

\\
��������� ���������� �����
const randomInt = (min, max) => Math.floor(Math.random() * (max - min +1) + min)
const randomColor = () => `rgb(${randomInt(0, 255)},${randomInt(0, 255)},${randomInt(0, 255)}) 

\\
������� ����� eventListener ��� ���� ���������
***����� forEach

document.querySelectorAll('.nav__link').forEach(function (element)
{
    element.addEventListener('click', function(event)
    {
        event.preventDefault()
        const id = this.getAttribute('href')
        document.querySelector(id).scrollIntoView({ behavior: 'smooth' })
    }
)})

*** ����� �������������
document.querySelector('�������� ��������').addEventListener('click', function(event)
{
    if (event.target.classList.contains('��������, �� ������� ����������� ��������'))
    {
        event.preventDefault()
        const id = event.target.getAttribute('href')
        document.querySelector(id).scrollIntoView({ behavior: 'smooth' })
    }
})

\\��� ��������� (����� �������������)

HTML

<div class="operations">
        <div class="operations__tab-container">
          <button
            class="btn operations__tab operations__tab--1 operations__tab--active"
            data-tab="1"
          >
            <span>01</span>Instant Transfers
          </button>
          <button class="btn operations__tab operations__tab--2" data-tab="2">
            <span>02</span>Instant Loans
          </button>
          <button class="btn operations__tab operations__tab--3" data-tab="3">
            <span>03</span>Instant Closing
          </button>
        </div>
<div

JS

const tabs = document.querySelectorAll('.operations-tab')
const tabsContsiner = document.querySelectorAll('.operations-tab-container')
const tabs = document.querySelectorAll('.operations__content')

tabsContainer.addEventListener('click', function (e)
{
  const clicked = e.target.closest('.operations__tab');

  // Guard clause
  if (!clicked) return;

  // Remove active classes
  tabs.forEach(t => t.classList.remove('operations__tab--active'));
  tabsContent.forEach(c => c.classList.remove('operations__content--active'));

  // Activate tab
  clicked.classList.add('operations__tab--active');

  // Activate content area
  document
    .querySelector(`.operations__content--${clicked.dataset.tab}`)
    .classList.add('operations__content--active');
});

\\ ������ ����� � ��������� ���� ����� �� ������ ��������
const handleHover = function (e) {
  if (e.target.classList.contains('nav__link')) {
    const link = e.target;
    const siblings = link.closest('.nav').querySelectorAll('.nav__link');
    const logo = link.closest('.nav').querySelector('img');

    siblings.forEach(el => {
      if (el !== link) el.style.opacity = this;
    });
    logo.style.opacity = this;
  }
};

// Passing "argument" into handler
nav.addEventListener('mouseover', handleHover.bind(0.5));
nav.addEventListener('mouseout', handleHover.bind(1));


///////////////////////////////////////
// Sticky navigation: Intersection Observer API
///////////////////////////////////////

*** ������� ������ 

1) ��������� ������� = ������, ������ ����� ������������ ��� �������� � ��������
const stickyNav = function (entries) {
  const [entry] = entries;
  // console.log(entry);

  if (!entry.isIntersecting) nav.classList.add('sticky');
  else nav.classList.remove('sticky');
};

2) ��������� ���� c ����������� ���� options
const observerOptions =
{
    root:null, \\�������, � �������� ���������� ����� ������� �� �������� �������� ��������, Null - � ������ ��������
    threshold:[0, 0,2], \\ �� ���� c 0 �� 20% ��������� �� ������ �������� ����� �������� ��� ������� 
    rootMargin: '-90px' \\ �� ������ 90 �������� �� ��������� 20 % ������� ��������    
}
3) ��������� ��� ��������
new observer = new IntersectionObserver
(observerCallback, observerOptions) 

4) ���������� �������� �� ������ �������
observer.observe(section1)

***
������ � ���������
const header = document.querySelector('.header');
const navHeight = nav.getBoundingClientRect().height;

const stickyNav = function (entries) {
  const [entry] = entries;
  // console.log(entry);

  if (!entry.isIntersecting) nav.classList.add('sticky');
  else nav.classList.remove('sticky');
};

const headerObserver = new IntersectionObserver(stickyNav, {
  root: null,
  threshold: 0,
  rootMargin: `-${navHeight}px`,
});

headerObserver.observe(header);

///////////////////////////////////////
// ��������� ������ ����� �� ��� ������� �������
///////////////////////////////////////

const allSections = document.querySelectorAll('.section');

const revealSection = function (entries, observer) {
  const [entry] = entries;

  if (!entry.isIntersecting) return;

  entry.target.classList.remove('section--hidden');
  observer.unobserve(entry.target);
};

const sectionObserver = new IntersectionObserver(revealSection, {
  root: null,
  threshold: 0.15,
});

allSections.forEach(function (section) {
  sectionObserver.observe(section);
  section.classList.add('section--hidden');
});
///////////////////////////////////////
// Lazy loading images
///////////////////////////////////////

const imgTargets = document.querySelectorAll('img[data-src]');

const loadImg = function (entries, observer) {
  const [entry] = entries;

  if (!entry.isIntersecting) return;

  // Replace src with data-src
  entry.target.src = entry.target.dataset.src;

  entry.target.addEventListener('load', function () {
    entry.target.classList.remove('lazy-img');
  });

  observer.unobserve(entry.target);
};

const imgObserver = new IntersectionObserver(loadImg, {
  root: null,
  threshold: 0,
  rootMargin: '200px',
});

imgTargets.forEach(img => imgObserver.observe(img));


///////////////////////////////////////
// Slider
///////////////////////////////////////




const slider = function () {
  const slides = document.querySelectorAll('.slide');
  const btnLeft = document.querySelector('.slider__btn--left');
  const btnRight = document.querySelector('.slider__btn--right');
  const dotContainer = document.querySelector('.dots');

  let curSlide = 0;
  const maxSlide = slides.length;

  // Functions
  const createDots = function () {
    slides.forEach(function (_, i) {
      dotContainer.insertAdjacentHTML(
        'beforeend',
        `<button class="dots__dot" data-slide="${i}"></button>`
      );
    });
  };

  const activateDot = function (slide) {
    document
      .querySelectorAll('.dots__dot')
      .forEach(dot => dot.classList.remove('dots__dot--active'));

    document
      .querySelector(`.dots__dot[data-slide="${slide}"]`)
      .classList.add('dots__dot--active');
  };

  const goToSlide = function (slide) {
    slides.forEach(
      (s, i) => (s.style.transform = `translateX(${100 * (i - slide)}%)`)
    );
  };

  // Next slide
  const nextSlide = function () {
    if (curSlide === maxSlide - 1) {
      curSlide = 0;
    } else {
      curSlide++;
    }

    goToSlide(curSlide);
    activateDot(curSlide);
  };

  const prevSlide = function () {
    if (curSlide === 0) {
      curSlide = maxSlide - 1;
    } else {
      curSlide--;
    }
    goToSlide(curSlide);
    activateDot(curSlide);
  };

  const init = function () {
    goToSlide(0);
    createDots();

    activateDot(0);
  };
  init();

  // Event handlers
  btnRight.addEventListener('click', nextSlide);
  btnLeft.addEventListener('click', prevSlide);

  document.addEventListener('keydown', function (e) {
    if (e.key === 'ArrowLeft') prevSlide();
    e.key === 'ArrowRight' && nextSlide();
  });

  dotContainer.addEventListener('click', function (e) {
    if (e.target.classList.contains('dots__dot')) {
      const { slide } = e.target.dataset;
      goToSlide(slide);
      activateDot(slide);
    }
  });
};
slider();


