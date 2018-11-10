---
title: 陳述式摘要
ms.date: 11/04/2016
ms.assetid: ce45d2fe-ec0e-459f-afb1-80ab6a7f0239
ms.openlocfilehash: ac5452e4b7e3faeff364d9f03ec7b87b3b82bd36
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491961"
---
# <a name="summary-of-statements"></a>陳述式摘要

*statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*labeled-statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*compound-statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*expression-statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*selection-statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*iteration-statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*jump-statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*try-except-statement* /\* Microsoft 專有 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*try-finally-statement* /\* Microsoft 專有 \*/

*jump-statement*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**goto**  *識別碼*  **;**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**繼續 ;**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**中斷 ;**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**return** *expression*<sub>opt</sub> **;**

*compound-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *declaration-list*<sub>opt</sub> *statement-list*<sub>opt</sub> **}**

*declaration-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*宣告*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-list* *宣告*

*statement-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*陳述式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement-list* *陳述式*

*expression-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*expression*<sub>opt</sub> **;**

*iteration-statement*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**while (**  *運算式*  **)**  *陳述式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**do**  *陳述式*  **while (**  *運算式*  **) ;**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**for (**  *運算式*<sub>opt</sub> **;** *運算式*<sub>opt</sub> **;** *運算式*<sub>opt</sub> **)** *陳述式*

*selection-statement*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**if (**  *運算式*  **)**  *陳述式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**if (**  *運算式*  **)**  *陳述式*  **else**  *陳述式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**switch (**  *運算式*  **)**  *陳述式*

*labeled-statement*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼*  **:**  *陳述式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**case**  *constant-expression*  **:**  *陳述式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**預設 :**  *陳述式*

*try-except-statement*:   /\* Microsoft 特定 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__try**  *compound-statement* **__except (**  *陳述式*  **)**  *compound-statement*

*try-finally-statement*:   /\* Microsoft 特定 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__try**  *compound-statement* **__finally**  *compound-statement*

## <a name="see-also"></a>請參閱

[階段結構文法](../c-language/phrase-structure-grammar.md)