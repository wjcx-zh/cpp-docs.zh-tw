---
title: 前置處理器文法
ms.date: 09/04/2018
helpviewer_keywords:
- preprocessor
- grammar, preprocessor
- preprocessor, grammar
ms.assetid: 6cd33fad-0b08-4592-9be8-7359c43e24e9
ms.openlocfilehash: 6177cf5fddba549e410842ef3f270edcc13d4782
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62179876"
---
# <a name="preprocessor-grammar"></a>前置處理器文法

*控制列*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#define** *identifier* *token-string*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#define** <em>identifier</em>**(** *identifier*<sub>opt</sub> **,** ... **,** *identifier*<sub>opt</sub> **)** *token-string*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#include** **"** *path-spec* **"**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#include** **\<** *path-spec* **>**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#line** *digit-sequence*  **"** *filename* **"**<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#undef** *identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#error** *token-string*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#pragma** *token-string*

*constant-expression*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**defined(** *identifier* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**defined** *identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;任何其他的常數運算式

*條件式*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*if-part* *elif-parts*<sub>opt</sub> *else-part*<sub>opt</sub> *endif-line*

*if-part* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*if-line* *text*

*if 程式行*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#if** *constant-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#ifdef** *identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#ifndef** *identifier*

*elif 部分*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*elif-line* *text*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*elif-parts* *elif-line* *text*

*elif 列*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#elif** *constant-expression*

*else 部分*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*else-line* *text*

*其他列*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#else**

*endif 列*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#endif**

*digit-sequence* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit-sequence* *digit*

*digit* : one of<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**

*語彙基元字串*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;語彙基元字串

*語彙基元*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*關鍵字*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*常數*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*運算子*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*標點符號*

*filename* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;合法的作業系統檔案名稱

*path-spec* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;合法的檔案路徑

*text* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;文字的任意序列

> [!NOTE]
> 要展開中的下列非終端[語彙慣例](../cpp/lexical-conventions.md)一節*C++語言參考*:*常數*， *常數運算式*，*識別項*，*關鍵字*，*運算子*，並*標點符號*。

## <a name="see-also"></a>另請參閱

[文法摘要 (C/C++)](../preprocessor/grammar-summary-c-cpp.md)