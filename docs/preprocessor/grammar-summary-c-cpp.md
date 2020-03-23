---
title: 前置處理器文法摘要 (C/C++)
description: 定義和描述 Microsoft C/C++編譯器（MSVC）預處理器文法語法。
ms.date: 08/29/2019
helpviewer_keywords:
- grammar
- preprocessor, grammar
ms.assetid: 0acb6e9b-364c-4ef8-ace4-7be980521121
ms.openlocfilehash: 68e5f09acfc6444afb46bcbc0f7e9db10b04afed
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076865"
---
# <a name="preprocessor-grammar-summary-cc"></a>前置處理器文法摘要 (C/C++)

本文說明 C 和C++預處理器的正式文法。 其中涵蓋前置處理指示詞和運算子的語法。 如需詳細資訊，請參閱[預處理器](../preprocessor/preprocessor.md)和 Pragma 指示詞[，以及 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)。

## <a name="definitions-for-the-grammar-summary"></a><a name="definitions"></a>文法摘要的定義

終端是語法定義的端點。 沒有其他解決方式。 終端包括一組保留字和使用者定義的識別項。

非終端在語法中是預留位置。 大部分是在此語法摘要中的其他位置定義。 定義可以是遞迴式。 下列非終端項定義于 *C++語言參考*的 [[詞彙慣例](../cpp/lexical-conventions.md)] 區段中：

*常數*、*常數運算式*、*識別碼*、*關鍵字*、*運算子*、*標點符號*

選擇性的元件會以下標的 <sub>opt</sub> 表示。 例如，下列語法表示以大括弧括住的選擇性運算式：

**{** *expression*<sub>opt</sub> **}**

## <a name="document-conventions"></a><a name="conventions"></a>檔慣例

許多慣例會針對語法的不同元件使用不同的字型屬性。 符號和字型如下：

| 屬性 | 描述 |
|---------------|-----------------|
| *nonterminal* | 斜體類型表示非終端項。 |
| **#include** | 粗體類型的終端項為必須依下述方式輸入的常值保留字和符號。 此內容中的字元一律區分大小寫。 |
| <sub>opt</sub> | 後面接著非終端項的 <sub>opt</sub> 一律為選擇項。|
| 預設字樣 | 集合中以這個字樣描述或列出的字元可以做為陳述式中的終端頂使用。 |

接著非終端項的冒號 ( **:** ) 會引入其定義。 替代定義則會在其他行列出。

在程式碼語法區塊中，預設字樣中的這些符號具有特殊意義：

| 符號 | 描述 |
|---|---|
| \[ ] | 方括弧會括住選擇性元素。 |
| {\|} | 大括弧括住以分隔號分隔的替代元素。 |
| ... | 表示可以重複先前的元素模式。 |

在程式碼語法區塊中，逗號（`,`）、句點（`.`）、分號（`;`）、冒號（`:`）、括弧（`( )`）、雙引號（`"`）和單引號（`'`）都是常值。

## <a name="preprocessor-grammar"></a><a name="grammar"></a>預處理器文法

*控制行*： \
&nbsp;&nbsp;&nbsp;&nbsp; **#define** *識別碼* *token-字串*<sub>opt</sub>\
&nbsp;&nbsp;&nbsp;&nbsp; **#define** *識別碼* **（** *identifier*<sub>opt</sub> **，** ... **，** *identifier*<sub>opt</sub> **）** *標記字串*<sub>opt</sub>\
&nbsp;&nbsp;&nbsp;&nbsp; **#include** **"** _path-spec_ **"** \
&nbsp;&nbsp;&nbsp;&nbsp; **#include** **\<** _路徑-規格_ **>** \
&nbsp;&nbsp;&nbsp;&nbsp; **#line** *數位順序* **"** _filename_ **"** <sub>opt</sub>\
&nbsp;&nbsp;&nbsp;&nbsp; **#undef** *識別碼*\
&nbsp;&nbsp;&nbsp;&nbsp; **#error** *token-字串*\
&nbsp;&nbsp;&nbsp;&nbsp; **#pragma** *token-字串*

*常數運算式*： \
**已定義**&nbsp;&nbsp;&nbsp;&nbsp;（*識別碼* **）** \
&nbsp;&nbsp;&nbsp;&nbsp;**定義**的*識別碼*\
&nbsp;&nbsp;&nbsp;&nbsp;任何其他常數運算式

*條件*式： \
&nbsp;&nbsp;&nbsp;&nbsp;*如果-part* *elif part*<sub>opt</sub> *else-part*<sub>opt</sub> *endif-line*

*if-part*： \
&nbsp;&nbsp;&nbsp;&nbsp;*的*單行*文字*

*如果-line*： \
&nbsp;&nbsp;&nbsp;&nbsp; **#if** *常數運算式*\
&nbsp;&nbsp;&nbsp;&nbsp; **#ifdef** *識別碼*\
&nbsp;&nbsp;&nbsp;&nbsp; **#ifndef** *識別碼*

*elif-元件*： \
&nbsp;&nbsp;&nbsp;&nbsp;*elif 行* *文字*\
&nbsp;&nbsp;&nbsp;&nbsp;*elif-part* *elif-line* *text*

*elif-line*： \
&nbsp;&nbsp;&nbsp;&nbsp; **#elif** *常數運算式*

*else-part*： \
&nbsp;&nbsp;&nbsp;&nbsp;*其他行* *文字*

*else-line*： \
&nbsp;&nbsp;&nbsp;&nbsp; **#else**

*endif-line*： \
&nbsp;&nbsp;&nbsp;&nbsp; **#endif**

*數位-序列*： \
&nbsp;&nbsp;&nbsp;&nbsp;*位數*\
&nbsp;&nbsp;&nbsp;&nbsp;*位數-序號* *digit*

*數位*：其中一個 \
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**

*token-字串*： \
&nbsp;&nbsp;&nbsp;權杖的 &nbsp;字串

*token*： \
&nbsp;&nbsp;&nbsp;&nbsp;*關鍵字*\
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼*\
&nbsp;&nbsp;&nbsp;&nbsp;*常數*\
&nbsp;&nbsp;&nbsp;&nbsp;*運算子*\
&nbsp;&nbsp;&nbsp;&nbsp;*標點符號*

*檔案名*： \
&nbsp;&nbsp;&nbsp;&nbsp;合法的作業系統檔案名

*路徑規格*： \
&nbsp;&nbsp;&nbsp;&nbsp;合法的檔案路徑

*文字*： \
&nbsp;&nbsp;&nbsp;&nbsp;任何一系列的文字

> [!NOTE]
> 下列非終端項會在 *C++語言參考*的 [[詞彙慣例](../cpp/lexical-conventions.md)] 區段中展開：*常數*、*常數運算式*、*識別碼*、*關鍵字*、*運算子*和*標點符號*。

## <a name="see-also"></a>另請參閱

[C/C++預處理器參考](../preprocessor/c-cpp-preprocessor-reference.md)
