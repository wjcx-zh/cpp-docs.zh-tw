---
title: 運算式的摘要
ms.date: 06/14/2018
ms.assetid: ed448953-687a-4b57-a1cb-12967bd770ea
ms.openlocfilehash: 320baa51d54f00ac4fdb6633922a8bb36cf92a94
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50543490"
---
# <a name="summary-of-expressions"></a>運算式的摘要

*primary-expression*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*常數*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*string-literal*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(**  *expression*  **)**

*expression*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*expression*  **,**  *assignment-expression*

*constant-expression*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*conditional-expression*

*conditional-expression*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-OR-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-OR-expression*  **?**  *expression*  **：**  *conditional-expression*

*assignment-expression*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*conditional-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unary-expression* *assignment-operator* *assignment-expression*

*postfix-expression*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*primary-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **[**  *運算式*  **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **(**  *argument-expression-list*<sub>opt</sub> **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **.**  *identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **->**  *識別碼*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **++**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **--**

*argument-expression-list*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*argument-expression-list*  **,**  *assignment-expression*

*unary-expression*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**++**  *unary-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**--**  *unary-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unary-operator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*cast-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**sizeof**  *unary-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**sizeof (**  *type-name*  **)**

*unary-operator*：下列其中一個<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**&** **&#42;** **+** **-** **~** **!**

*cast-expression*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unary-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(**  *type-name*  **)**  *cast-expression*

*multiplicative-expression*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*cast-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplicative-expression*  **&#42;**  *cast-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplicative-expression*  **/**  *cast-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplicative-expression*  **%**  *cast-expression*

*additive-expression*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplicative-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*additive-expression*  **+**  *multiplicative-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*additive-expression*  **-**  *multiplicative-expression*

*shift-expression*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*additive-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*shift-expression*  **\<\<**  *additive-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*shift-expression*  **>>**  *additive-expression*

*relational-expression*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression*  **\<**  *shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression*  **>**  *shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression*  **\<=**  *shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression*  **>=**  *shift-expression*

*equality-expression*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*equality-expression*  **==**  *relational-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*equality-expression*  **!=**  *relational-expression*

*AND-expression*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*equality-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*AND-expression*  **&**  *equality-expression*

*exclusive-OR-expression*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*AND-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*exclusive-OR-expression*  **^**  *AND-expression*

*inclusive-OR-expression*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*exclusive-OR-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*inclusive-OR-expression*  **&#124;**  *exclusive-OR-expression*

*logical-AND-expression*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*inclusive-OR-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-AND-expression*  **&&**  *inclusive-OR-expression*

*logical-OR-expression*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-AND-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-OR-expression*  **&#124;&#124;**  *logical-AND-expression*

## <a name="see-also"></a>另請參閱

- [階段結構文法](../c-language/phrase-structure-grammar.md)
