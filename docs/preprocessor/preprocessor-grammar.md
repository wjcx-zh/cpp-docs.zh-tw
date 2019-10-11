---
title: 前置處理器文法
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor
- grammar, preprocessor
- preprocessor, grammar
ms.assetid: 6cd33fad-0b08-4592-9be8-7359c43e24e9
ms.openlocfilehash: f0916e3cc9bbdb398db693286dacc4517df03557
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222255"
---
# <a name="preprocessor-grammar"></a>前置處理器文法

*控制行*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#define** *識別碼* *token-字串*<sub>opt</sub>\
&nbsp;&nbsp;&nbsp;&nbsp; **#define** *識別碼* **(** &#x2800;identifier&#x200B;<sub>opt</sub> **,** ... **,** *識別碼*&#x200B; <sub> </sub>opt&#x2800; **)** *token-字串*<sub>opt</sub>\
&nbsp;&nbsp;&nbsp;&nbsp; **#include** **"** _路徑-規格_ **"** \
&nbsp;&nbsp;&nbsp;&nbsp; **#include**_路徑-規格_ **\<** **>** \
&nbsp;&nbsp;&nbsp;&nbsp; **#line** *數位順序* **"** _檔案名_ **"** &#x200B; <sub>opt</sub>  \
&nbsp;&nbsp;&nbsp;&nbsp; **#undef** *識別碼*\
&nbsp;&nbsp;&nbsp;&nbsp; **#error** *token-字串*\
&nbsp;&nbsp;&nbsp;&nbsp; **#pragma** *token-string*

*常數運算式*: \
&nbsp;&nbsp;&nbsp;&nbsp;**已定義 (** &#x2800;*識別碼*&#x2800; **)** \
&nbsp;&nbsp;&nbsp;&nbsp;**已定義** *識別碼*\
&nbsp;&nbsp;&nbsp;&nbsp;任何其他常數運算式

*條件*式: \
&nbsp;&nbsp;&nbsp;&nbsp;*if-part* *elif-元件*<sub>opt</sub>*其他-部分*<sub>opt</sub>*endif-行*

*if-part*: \
&nbsp;&nbsp;&nbsp;&nbsp;*若為-line* *文字*

*如果-line*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#if** *常數運算式*\
&nbsp;&nbsp;&nbsp;&nbsp; **#ifdef** *識別碼*\
&nbsp;&nbsp;&nbsp;&nbsp; **#ifndef** *識別碼*

*elif-元件*: \
&nbsp;&nbsp;&nbsp;&nbsp;*elif-行* *文字*\
&nbsp;&nbsp;&nbsp;&nbsp;*elif-元件* *elif-行* *文字*

*elif-line*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#elif** *constant-expression*

*else-part*: \
&nbsp;&nbsp;&nbsp;&nbsp;*其他-行* *文字*

*else-line*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#else**

*endif-line*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#endif**

*數位-序列*: \
&nbsp;&nbsp;&nbsp;&nbsp;*八進位*\
&nbsp;&nbsp;&nbsp;&nbsp;*digit-sequence* *digit*

*數位*: 其中一個 \
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**

*token-字串*: \
&nbsp;&nbsp;&nbsp;&nbsp;標記的字串

*token*: \
&nbsp;&nbsp;&nbsp;&nbsp;*關鍵字*\
&nbsp;&nbsp;&nbsp;&nbsp;*標識*\
&nbsp;&nbsp;&nbsp;&nbsp;*常數*\
&nbsp;&nbsp;&nbsp;&nbsp;*操作*\
&nbsp;&nbsp;&nbsp;&nbsp;*標點符號*

*檔案名*: \
&nbsp;&nbsp;&nbsp;&nbsp;合法的作業系統檔案名

*路徑規格*: \
&nbsp;&nbsp;&nbsp;&nbsp;合法的檔案路徑

*文字*: \
&nbsp;&nbsp;&nbsp;&nbsp;任何文字順序

> [!NOTE]
> 下列非終端項會在 *C++語言參考*的 [[詞彙慣例](../cpp/lexical-conventions.md)] 區段中展開:*常數*、*常數運算式*、*識別碼*、*關鍵字*、*運算子*和*標點符號*。

## <a name="see-also"></a>另請參閱

[文法摘要 (C/C++)](../preprocessor/grammar-summary-c-cpp.md)
