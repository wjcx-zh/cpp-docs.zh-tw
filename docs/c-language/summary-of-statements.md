---
title: 陳述式摘要
ms.date: 11/04/2016
ms.assetid: ce45d2fe-ec0e-459f-afb1-80ab6a7f0239
ms.openlocfilehash: 122c79b53a8af8a384097dec51a14746a090b1cf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220791"
---
# <a name="summary-of-statements"></a>陳述式摘要

*語句*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*加上標籤的語句*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*複合陳述式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*expression 語句*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*選取範圍-語句*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*反復專案語句*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*跳躍語句*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*try-except-語句*  / \*Microsoft 特定\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*try-catch-finally 語句*  / \*Microsoft 特定\*/

*跳躍語句*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`goto`**  *識別碼*  **;**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**持續**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**崩潰**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`return`***運算式*<sub>opt</sub> **;**

*複合陳述式*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{宣告** *-列出*<sub>opt</sub> *語句清單*<sub>opt</sub> **}**

*declaration-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*清點*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-list* *宣告*

*statement-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*句*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement-list* *陳述式*

*運算式語句*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*expression*<sub>opt</sub> **;**

*反復專案語句*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**while （**  *運算式*  **）**  *語句*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`do`**  *語句*  **while （**  *運算式*  **）;**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**for （**  *expression*<sub>opt</sub> **;** *運算式*<sub>opt</sub> **;** *運算式*<sub>opt</sub> **）** *語句*

*選取範圍-語句*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**if （**  *expression*  **）**  *語句*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**if （***運算式***）***語句* **`else`** *語句*          <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**switch （**  *expression*  **）**  *語句*

加上*標籤的語句*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*  **：**  *語句*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`case`**  *常數運算式*  **：**  *語句*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**預設 :**  *陳述式*

*try-except-語句*：/ \* Microsoft 專有\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__try**  *複合陳述式* **__except （**  *expression*  **）**  *複合陳述式*

*try-catch-finally 語句*：/ \* Microsoft 專有\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__try***複合陳述式* **`__finally`** *複合陳述式*    

## <a name="see-also"></a>另請參閱

[片語結構文法](../c-language/phrase-structure-grammar.md)
