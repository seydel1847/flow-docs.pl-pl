---
title: Używanie języka Markdown do formatowania zatwierdzeń usługi Microsoft Flow | Microsoft Docs
description: Dowiedz się, jak używać języka Markdown do formatowania żądań zatwierdzenia w usłudze Microsoft Flow.
services: ''
suite: flow
documentationcenter: na
author: gcorvera
manager: kfile
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 4/23/2018
ms.author: gcorvera
ms.openlocfilehash: dc8d9d650b02b7962770ff0574deb151492739d9
ms.sourcegitcommit: 4a8d11e1768cd0ca96a60b6f5548a68c0c8999e5
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/12/2018
ms.locfileid: "32323637"
---
# <a name="use-markdown-in-microsoft-flow-approval-requests"></a>Używanie języka Markdown w żądaniach zatwierdzenia w usłudze Microsoft Flow

Ten artykuł zawiera wskazówki dotyczące używania składni języka [Markdown](https://en.wikipedia.org/wiki/Markdown) do dodawania bogatego formatowania i tabel do żądań zatwierdzenia.

## <a name="headers"></a>Nagłówki

Utwórz strukturę komentarzy przy użyciu nagłówków. Dłuższe komentarze w nagłówkach są dzielone na segmenty, dzięki czemu można je łatwiej odczytać.

Rozpocznij wiersz od znaku skrótu `#`, aby ustawić nagłówek. Zorganizuj uwagi przy użyciu nagłówków podrzędnych, rozpoczynając wiersz dodatkowymi znakami skrótów, na przykład `####`. Maksymalna liczba obsługiwanych poziomów nagłówków to sześć.

**Przykład:**

```Markdown
# This is a H1 header
## This is a H2 header
### This is a H3 header
#### This is a H4 header
##### This is a H5 header
```

**Wynik:**

![Eksportowanie przepływu](./media/approvals-markdown-support/mrkdown-headers.png)

## <a name="paragraphs-and-line-breaks"></a>Akapity i znaki końca wiersza

Zwiększ czytelność tekstu przez podzielenie go przy użyciu akapitów lub znaków końca wiersza. Wprowadź dwie spacje przed znakiem końca wiersza, aby rozpocząć nowy akapit, lub wprowadź dwa znaki końca wiersza po kolei, aby rozpocząć nowy akapit.   
   
**Przykład**

<pre>
Add lines between your text with the Enter key.
This spaces your text better and makes it easier to read.
</pre>

**Wynik:**   
Dodaj wiersze w tekście przy użyciu klawisza Enter.      
Spowoduje to lepsze rozmieszczenie tekstu i zwiększenie jego czytelności.


**Przykład 2**

<pre>
Add two spaces prior to the end of the line.(space, space)     
This adds space in between paragraphs.
</pre>

**Wynik:**  
Dodaj dwie spacje przed końcem wiersza.   

Spowoduje to dodanie miejsca między akapitami.
  

## <a name="lists"></a>Listy

Listy umożliwiają organizowanie powiązanych elementów. Można dodawać listy uporządkowane z liczbami lub listy nieuporządkowane zawierające tylko punktory.

Listy uporządkowane rozpoczynają się liczbą z kropką dla każdego elementu listy. Listy nieuporządkowane rozpoczynają się symbolem `*`. Rozpocznij każdy element listy w nowym wierszu. W pliku lub widgecie języka Markdown wprowadź dwie spacje przed znakiem końca wiersza, aby rozpocząć nowy akapit, lub wprowadź dwa znaki końca wiersza po kolei, aby rozpocząć nowy akapit.   

### <a name="ordered-or-numbered-lists"></a>Listy uporządkowane lub numerowane

**Przykład:**

```Markdown
0. First item.
0. Second item.
0. Third item.
```

**Wynik:**

1. Pierwszy element.
2. Drugi element.
3. Trzeci element.

### <a name="bullet-lists"></a>Listy wypunktowane

**Przykład:**

<pre>

- Item 1
- Item 2
- Item 3

</pre>

**Wynik:**

- Element 1
- Element 2
- Element 3

### <a name="nested-lists"></a>Listy zagnieżdżone

**Przykład:**
<pre>

1. First item.
   - Item 1
   - Item 2
   - Item 3
1. Second item.
   - Nested item 1
   - Nested item 2
   - Nested item 3

</pre>

**Wynik:**  

1. Pierwszy element.

    - Element 1
    - Element 2
    - Element 3
2. Drugi element.
    - Element zagnieżdżony 1
    - Element zagnieżdżony 2
    - Element zagnieżdżony 3


## <a name="links"></a>Linki

Adresy URL protokołów HTTP i HTTPS są automatycznie formatowane jako linki. 

Tekst hiperlinków można ustawić dla adresu URL przy użyciu standardowej składni linków w języku Markdown:

```Markdown
[Link Text](Link URL)
```

**Przykład:**
<pre>
&#91;Microsoft Flow](https://flow.microsoft.com)
</pre>

**Wynik:**

[Microsoft Flow](https://flow.microsoft.com)

### <a name="anchor-links"></a>Linki kotwiczące

Identyfikatory zakotwiczeń są przypisywane do wszystkich nagłówków renderowanych w formacie HTML. Identyfikator to składający się z samych małych liter tekst nagłówka, w którym spacje zastąpiono kreskami (-).

**Przykład:**

<pre>
###Link to a heading in the page
</pre>

<br/>

**Wynik:**

Składnia linku kotwiczącego do sekcji...

<pre>
[Link to a heading in the page](#link-to-a-heading-in-the-page)
</pre> 
<br/>
Identyfikator składa się z samych małych liter, a link uwzględnia wielkość liter, dlatego należy używać małych liter, nawet jeśli w samym nagłówku są używane wielkie litery.


## <a name="tables"></a>Tabele

Tabele umożliwiają organizowanie danych o określonej strukturze. 

- Umieść każdy wiersz tabeli w osobnym wierszu 
- Oddziel komórki tabeli przy użyciu znaku kreski pionowej `|` 
- Dwa pierwsze wiersze służą do ustawiania nagłówków kolumn i sposobu wyrównywania elementów w tabeli
- Użyj średników (`:`) w przypadku dzielenia nagłówka i treści tabeli w celu określenia wyrównania kolumn (lewo, środek, prawo) 
- Aby rozpocząć nowy wiersz, użyj tagu podziału HTML (`<br/>`) (działa w witrynie typu wiki, ale nie w innych miejscach)  
- Upewnij się, że każdy wiersz kończy się znakiem CR lub LF. 

**Przykład:**

<pre>
| Heading 1 | Heading 2 | Heading 3 |  
|-----------|:-----------:|-----------:|  
| Cell A1 | Cell A2 | Cell A3 |  
| Cell B1 | Cell B2 | Cell B3<br/>second line of text |  
</pre>  <br/>

**Wynik:**  

| Nagłówek 1 | Nagłówek 2 | Nagłówek 3 |  
|-----------|:---------:|-----------:|  
| Komórka A1 | Komórka A2 | Komórka A3 |  
| Komórka B1 | Komórka B2 | Komórka B3<br/>drugi wiersz tekstu |  

 
## <a name="emphasis-bold-italics-strikethrough"></a>Wyróżnienie (pogrubienie, kursywa, przekreślenie)  

Aby wyróżnić tekst, możesz zastosować do znaków pogrubienie, kursywę lub przekreślenie: 
- Aby zastosować kursywę: umieść tekst między znakami gwiazdki `*` lub podkreślenia `_`.   
- Aby zastosować pogrubienie: umieść tekst między znakami dwóch gwiazdek `**`.    
- Aby zastosować przekreślenie: umieść tekst między znakami dwóch tyld `~~`.   

Połącz te elementy, aby zastosować do tekstu różne rodzaje wyróżnienia.    

**Przykład:**

<pre>
Use _emphasis_ in comments to express **strong** opinions and point out ~~corrections~~ 
**_Bold, italicized text_**  
**~~Bold, strike-through text~~**
</pre>

<br/>

**Wynik:**

Użyj _wyróżnienia_ w komentarzach, aby wyrazić **zdecydowane** opinie i wskazać <s>poprawki</s>   
**_Pogrubiony tekst pisany kursywą_**   
**~~Pogrubiony przekreślony tekst~~**  


## <a name="special-characters"></a>Znaki specjalne

<table width="650px">
<tbody valign="top">
<tr>
<th width="300px">Składnia</th>
<th width="350px">Przykład/uwagi</th>
</tr>



<tr>
<td>
<p>Aby wstawić jeden z następujących znaków, użyj prefiksu w postaci ukośnika odwrotnego:</p>

<p style="margin-bottom:2px;">```\   backslash ``` </p>
<p style="margin-bottom:2px;"><code>\`</code>   `backtick`</p>
<p style="margin-bottom:2px;">```_   underscore  ```</p>
<p style="margin-bottom:2px;">```{}  curly braces  ``` </p>
<p style="margin-bottom:2px;">```[]  square brackets ```</p>
<p style="margin-bottom:2px;">```()  parentheses  ```</p>
<p style="margin-bottom:2px;">```#   hash mark  ``` </p>
<p style="margin-bottom:2px;">```+   plus sign  ```</p>
<p style="margin-bottom:2px;">```-   minus sign (hyphen) ```</p>
<p style="margin-bottom:2px;">```.   dot  ``` </p>
<p style="margin-bottom:2px;">```!   exclamation mark ```</p>


</td>
<td>Kilka przykładów wstawiania znaków specjalnych
<p>Wprowadź ```\\```, aby uzyskać \\ </p>
<p>Wprowadź ```\_```, aby uzyskać _ </p>
<p>Wprowadź ```\#```, aby uzyskać \# </p>
<p>Wprowadź ```\(```, aby uzyskać \( </p>
<p>Wprowadź ```\.```, aby uzyskać \. </p>
<p>Wprowadź ```\!```, aby uzyskać \! </p>
</td>
</tr>

</tbody>
</table>
