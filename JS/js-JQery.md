
********
JQuery
********

Google CDN. �������� ���� ������ �� ���� JS.

<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>

���������:

$
=
jQuery();

���� ������ ��������� � head:
$(document).ready(function()
{
$('h1').css('color', 'red');
});

��� ������ ��������� �� � ����� body.

������ ����������:
* ������ document.querySelector("h1");

����� ������ $('h1');

*������ document.querySelectorAll("button");    
    
����� ������ $("button"); 

* ��� ����������� �� ������� ������� ������ 
$('��������').css("color", "green");

* ��� ������ �������� � �������:
console.log($("h1").css("font-size");

* ��� ���������� ������ ������:
$("h1").addClass("big-title");

* ��� ���������� ���� ����� �������:
$("h1").addClass("big-title margin-50");

* �������� ������:
$("h1").removeClass("big-title");

* ��������� � ������� ����� �� ������ �����.
$("h1").hasClass("margin-50");

* ������ ����� �������:
$("h1").text("Bye");

* ������ ����� ������� � ���������:
$("button").html("<em>Bye</em>");

********
����������� � ����������
********

* ������ ������� �� �������
console.log($("img").attr("src"));

$("a").attr("href", "https://www.yahoo.com");

* ������ ����� �� �������
$("h1").attr("class");

********
���������� �������
********

$("h1").click(function() 
{
    $("h1").css("color", "purple");
});


������ JS: 
for (var i = 0; i < 5; i++)
{
document.querySelectorAll("button")[i].addEventListener("click", function()
    {
        document.querySelector("h1").style.color = "purple";
    });
}

����� ������:

$("button").click(function()
{
    $("h1").css("color", "purple");
});

* ���������� ������ ��� ������� �������

$("body").keypress(function(event)
{
    console.log(event.key);
});

* ������ ������ �� �������� ���������
$("body").keypress(function(event)
{
    $("h1").text(event.key);
});

* ���������� ������� �� �������� �����
$(h1).on("mouseover", function()
{
    $("h1").css("color", "purple");
});

$(h1).on("click", function()
{
    $("h1").css("color", "purple");
});

* ���������� ���������

�� � ����� ���� h1

$("h1").before("<button>New</button>");
$("h1").after("<button>New</button>");

�� � ����� �������� ������ ���� h1

$("h1").prepend("<button>New</button>");
$("h1").append("<button>New</button>");

* �������� ���������

* ������:

$("button").remove();
$("h1").gide();
$("h1").show();
$("h1").toggle();

* ������:

$("h1").fadeOut();
$("h1").fadeIn();
$("h1").fadeToggle();

* C������:

$("h1").slideUp();
$("h1").slideDown();
$("h1").slideToggle();

* ��������:

$("h1").animate({opacity: 0.5});

* �����������:
$("h1").slideUp().slideDown().animate({opacity: 0.5});

*******
�������
*******

* ������� � for.
for(var i=0; i<posts.length; i++)
{ 
    console.log(posts[i].title);
}; 

��� 

* ������� � forEach

posts.forEach(function(post){console.log(post.title)});

*******
���������� �������� ����
*******

* ������������ ���������� lodash

������

const requestedTitle = _.lowerCase(req.params.test);

���

const storedTitle = _.lowerCase(post.title);


