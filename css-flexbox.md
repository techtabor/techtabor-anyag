A CSS-ben az eredeti eszközökkel meglehetősen nehéz az elemek speciális elrendezése. Tipikusan még valami olyan könnyűnek tűnő feladat is, mint egy elem középre igazítása \(egyszerre vízszintesen és függőlegesen\), gondot okoz.

Azonban a CSS3-ban megjelent a _Flexbox,_ amivel az elemek dinamikus és pontos elrendezése lényegesen könnyebb lett. Ehhez tartozik egy kitűnő leírás, melyet [ezen a weblapon](https://css-tricks.com/snippets/css/a-guide-to-flexbox/) találtok.

{% exercise %}
Define a variable `x` equal to 10.
{% initial %}
var x =
{% solution %}
var x = 10;
{% validation %}
assert(x == 10);
{% context %}
// This is context code available everywhere
// The user will be able to call magicFunc in his code
function magicFunc() {
    return 3;
}
{% endexercise %}

