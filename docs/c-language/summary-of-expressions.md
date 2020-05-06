---
title: 運算式的摘要
ms.date: 06/14/2018
ms.assetid: ed448953-687a-4b57-a1cb-12967bd770ea
ms.openlocfilehash: 320baa51d54f00ac4fdb6633922a8bb36cf92a94
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157814"
---
# <a name="summary-of-expressions"></a>運算式的摘要

*主要-運算式*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*標識*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*常數*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*字串常值*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**（**  *運算式*  **）**

*expression*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*指派-運算式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*運算式*  **，**  *指派運算式*

*常數運算式*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*條件運算式*

*條件運算式*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-OR-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*邏輯 OR 運算式*  **？**  *expression*  **：**  *條件運算式*

*assignment-expression*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*條件運算式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unary-expression* *assignment-operator* *assignment-expression*

後置*運算式*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*primary-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;後置*運算式***[***運算式***]**      <br/>
&nbsp;&nbsp;&nbsp;&nbsp;後置*運算式***（***引數運算式清單*<sub>opt</sub> **）**    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;後置*運算式***。**    *識別碼 (identifier)*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*後置運算式*  **->**  *識別碼*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*後置運算式*  **++**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*後置運算式*  **--**

*argument-expression-list*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*指派-運算式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*引數-運算式-清單*  **，**  *指派運算式*

*一元運算式*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*後置運算式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**++**  *一元運算式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**--**  *一元運算式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*一元運算子*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*cast-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**sizeof**  *unary-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**sizeof (**  *type-name*  **)**

*unary-operator*：下列其中一個<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**&****&#42;** **+**&#42;**-** **!** ！ **~**

*cast-運算式*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*一元運算式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**（**  *類型名稱*  **）**  *cast 運算式*

*乘法運算式*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*cast-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplicative-expression*  **&#42;**  *cast-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*乘法運算式*  **/**  *轉換運算式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*乘法運算式*  **%**  *轉換運算式*

*加法類運算式*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplicative-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*加法運算式*  **+**  *乘法運算式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*加法運算式*  **-**  *乘法運算式*

*移位-運算式*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*additive-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*移位運算式***\<***加法運算式*    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*移位運算式*  **>>**  *加法運算式*

*關聯式運算式*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*關聯式運算式*  **\<**  *移位運算式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*關聯式運算式*  **>**  *移位運算式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*關聯式運算式***\<***移位運算式*    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*關聯式運算式*  **>=**  *移位運算式*

*equality-expression*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*相等運算式*  **==**  *關聯式運算式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*equality-expression*  **!=**  *relational-expression*

*AND-expression*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*等號比較運算式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*和-運算式*  **&**  *等號比較運算式*

*exclusive-OR-expression*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*和-運算式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*互斥 OR 運算式*  **^**  *和運算式*

*inclusive-OR-expression*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*互斥 OR 運算式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*inclusive-OR-expression*  **&#124;**  *exclusive-OR-expression*

*邏輯 AND 運算式*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*內含 OR 運算式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*邏輯 AND 運算式*  **&&**  *包含 OR 運算式*

*邏輯 OR 運算式*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*邏輯 AND 運算式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*邏輯 OR 運算式*  **&#124;&#124;**  *的邏輯 AND 運算式*

## <a name="see-also"></a>請參閱

- [片語結構文法](../c-language/phrase-structure-grammar.md)
