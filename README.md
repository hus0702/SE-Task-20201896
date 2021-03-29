# 확장 구문 - GitHub Flavored Markdown (GFM)

---

## **1. 테이블**<br>
## **2. Task list items**<br>
## **3. 취소선**<br>
## **4. 오토링크**<br>
## **5. Disallowed Raw HTML**<br>



<br><br><br><br>

---

## **1. 테이블**
테이블은 행과 열로 이루어진 배열입니다. 

맨 윗 행이 테이블의 헤더에 해당하며, 구분자 행(delimiter row)이 헤더와 다른 데이터를 구분합니다.

각 행은 임의의 텍스트를 포함하는 셀로 구성되며, 파이프\(\|)로 각 셀이 구분됩니다.

> 예시 코드 :
>
>       | 헤더1 | 헤더2 |
>       | --- | --- |
>       | 내용1 | 내용2 |
>       
>렌더링된 출력 :
>| 헤더1 | 헤더2 |
>| --- | --- |
>| 내용1 | 내용2 |
<br><br>

또한, 테이블의 구분자 행을 수정해서 가운데정렬, 오른쪽정렬, 왼쪽정렬등의 작업을 수행할 수 있습니다.

| 왼쪽정렬 | 가운데정렬 | 오른쪽정렬 |
|  :---  | :---: | ---: |
|abc | abc | abc |
| \:\-\-\-  | \:\-\-\-\: | \-\-\-\: |

<br><br>
## **테이블을 만들 때의 유의사항**

<br>

테이블은 블럭 수준의 구조를 셀에 포함시킬 수 없습니다. 따라서 해당 구조를 만나게 되면 테이블은 끊어집니다.

> 예시 코드 :
>
>       | abc | def |
>       | --- | --- |
>       bar | bar |
>       bar
>
>       | bar

렌더링된 출력 :

| abc | def |
| --- | --- |
bar | bar |
>bar

| bar

<br><br>

또한, 테이블은 헤더 행의 셀 수와 구분자 행의 개수를 맞춰줘야 합니다. 그렇지 않을 경우, 테이블은 인식되지 않습니다.

> 예시 코드 :
> 
>     | abc | def |
>     | --- |
>     | bar |
>     
> 렌더링된 출력 :
> 
> | abc | def |
> | --- |
> | bar |

<br>

구분자 행과 헤더 행의 셀의 개수만 일치한다면, 나머지 요소의 개수와 상관없이 테이블이 각각의 요소를 정렬할 수 있습니다.

<br><br><br><br>

---

## **2. Task List Items**
Task List Items는 문서 작성자가 만들 수 있는 일종의 체크리스트 항목입니다.

단, 이 기능은 체크박스가 어떤 대상과 상호작용을 하는것을 정의하지 않았기 때문에 직접 체크박스와의 상호작용은 어렵습니다.

따라서 체크박스에 해당하는 [ ] 에 작성자가 직접 X를 넣거나 빈칸으로 유지하는 것으로 체크박스를 제어할 수 있습니다.

> 예시 코드 :
>
>      - [ ]foo
>      - [x] bar
>         - [ ] baz
>      - [ ] bim  
>      
>렌더링된 출력 :
>
> - [ ] foo
> - [x] bar
>    - [ ] baz
>- [ ] bim  

<br><br><br><br>

---

## **3. 취소선**
어떤 텍스트에 취소선을 긋고 싶다면 그 텍스트를 (\~\~) 로 묶으면 됩니다.

> 예시 코드 :
> 
>     하루종일 과제만 하고 있습니다.~~과제좀 미리미리 할걸~~
>     
>렌더링된 출력 :
>
>하루종일 과제만 하고 있습니다.~~과제좀 미리미리 할걸~~
>

<br>
 
* 이 때, 취소선을 긋는 텍스트는 반드시 같은 라인에 있어야 합니다. 단락을 건너뛰면서 취소선을 긋고자 하는 경우 각 라인마다 따로 처리를 해주어야 합니다.

<br><br><br><br>

---

## **4. 오토링크**

www 오토링크는 텍스트 www. 가 ***유효한 도메인*** 과 함께 되었을 때 작동합니다.

유효한 도메인은 영문&숫자, \(\_\), \(\-\)로 구성되며 \(\.\)으로 인해 구분됩니다.

최소 한 개의 . 이 있어야 하며, 도메인의 마지막 두 부분은 \_가 올 수 없습니다.

> 예시 도메인 :
> 
>     www.example.org
>
>렌더링된 출력 :
>
> www.example.org

<br>

유효한 도메인 이후엔 **공백이나 <를 제외한** 문자가 올 수 있습니다.
> 예시 : 더 자세한 정보를 원하신다면 www.information.org/help 로 방문해주세요!

* 후행 구두점 (\?, \!, (\.), (\,), (\:), (\*), (\_), \~ ) 은 링크에 포함될 수는 있으나, 오토링크의 부분으로 인식되지는 않습니다.
> 예시 : www.abc.chocolate/a.b..?!

<br><br>

만약 오토링크가 \)로 끝난다면, GFM은 오토링크에 있는 괄호의 수를 검사합니다. 만약, '(' 보다 ')'가 더 많다면 그 )들은 일반 텍스트 처리가 됩니다.

> 예시 코드 : 
> 
>      www.google.com/search?q=Markup+(business)
>    
>      www.google.com/search?q=Markup+(business)))
>    
>      (www.google.com/search?q=Markup+(business))
>     
>      (www.google.com/search?q=Markup+(business)
>    
> 렌더링된 출력 : 
> 
> www.google.com/search?q=Markup+(business)
> 
> www.google.com/search?q=Markup+(business)))
> 
> (www.google.com/search?q=Markup+(business))
> 
> (www.google.com/search?q=Markup+(business)
> 

* 단, 이 규칙은 링크가 오직 ')'로 끝나는 경우에만 실행됩니다. 그렇지 않은 경우, 특별한 규칙이 적용되지 않습니다.

> 예시 코드 :
> 
>       www.google.com/search?q=(business))
>       
>       www.google.com/search?q=(business))^w^
>       
> 렌더링된 출력 :
> 
> www.google.com/search?q=(business))
>       
> www.google.com/search?q=(business))^w^

<br><br>

만약 오토링크가 세미콜론(;)으로 끝난다면, GFM은 링크에서 &를 찾고, 이 이후에 하나 이상의 알파벳이 있을 경우 이 알파벳을 링크에서 제외합니다.

> 예시 코드 :
> 
>       www.google.com/search?q=commonmark&hl=en
>       
>       www.google.com/search?q=commonmark&hl;
>
>렌더링된 출력 :
>
>www.google.com/search?q=commonmark&hl=en
>
>www.google.com/search?q=commonmark&hl;

<br><br>

만약 오토링크에 < 가 들어간다면 그 즉시 오토링크는 종료됩니다.
> 예시 코드 :
> 
>       www.commonmark.org/he<lp
>       
>렌더링된 출력:
>
>www.commonmark.org/he<lp

<br><br>

## 확장된 자동 링크
확장된 URL 오토링크는 http:// 혹은 https:// 가 유효한 도메인과 같이 발견되었으며, 공백이나 <를 제외한 0개 이상의 단어가 있을 때 생성됩니다.
> 예시 도메인 :
> 
>       https://example.org
>       
>       (Visit https://example.org/search?q=example+(business))
>       
>렌더링된 출력:
>
>https://example.org
>
> (Visit https://example.org/search?q=example+(business))

<br><br>

확장된 이메일 오토링크는 다음 규칙을 따르는 유효한 이메일 주소가 발견되었을 때 생성됩니다.
* 하나 혹은 그 이상의 알파벳이나 . , - , _ , + 가 포함되어야 함.
* @가 발견되어야 함.
* 하나 혹은 그 이상의 단어들이 점(.)에 의해 구분되어야 함. 최소한 . 하나는 있어야 함.
* 가장 마지막 단어가 -나 \_면 안 됨.
  > example@ex.kr_
  > 
  > example@ex.kr 
* +는 @ 전에만 올 수 있음.
  > example@e+x.kr
  > 
  > exam+@ex.kr
* 기호중에서는 오직 . 만이 주소의 끝에 올 수 있음.
  > example@ex.kr.
  > 
  > example@ex.kr_
  
  






