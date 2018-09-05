---
title: 前置處理器文法 |Microsoft Docs
ms.custom: ''
ms.date: 09/04/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- preprocessor
- grammar, preprocessor
- preprocessor, grammar
ms.assetid: 6cd33fad-0b08-4592-9be8-7359c43e24e9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 56df4d0bfdaf87ace87a9f9dcbde85166929e642
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43766112"
---
# <a name="preprocessor-grammar"></a>前置處理器文法

*控制列*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#define** *識別項**語彙基元字串*<sub>選擇</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#define** <em>識別項</em>**(** *識別碼*<sub>選擇</sub> **，** ...**，** *識別項*<sub>選擇</sub> **)** *語彙基元字串*<sub>選擇</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#include** **"** *路徑規格* **"**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#include** **\<** *路徑規格* **>**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#line** *數字序列***」** *filename* **"**<sub>選擇  </sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#undef** *識別碼*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#error** *語彙基元字串*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#pragma** *語彙基元字串*

*constant-expression*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**定義 (** *識別項* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**定義***識別碼*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;任何其他的常數運算式

*條件式*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*if 部分* *elif 部分*<sub>opt</sub> *else 部分*<sub>選擇</sub> *endif 列*

*if 部分*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*如果線條**文字*

*if 程式行*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#if** *常數運算式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#ifdef** *識別碼*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#ifndef** *識別碼*

*elif 部分*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*elif 單行**文字*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*elif 部分* *elif 列**文字*

*elif 列*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#elif** *常數運算式*

*else 部分*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*其他列**文字*

*其他列*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#else**

*endif 列*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#endif**

*數字序列*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*數字*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*數字序列**數字*

*數字*： 其中一個<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**

*語彙基元字串*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;語彙基元字串

*語彙基元*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*關鍵字*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*識別項*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*常數*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*運算子*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*標點符號*

*檔名*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;合法的作業系統檔案名稱

*路徑規格*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;合法的檔案路徑

*文字*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;文字的任意序列

> [!NOTE]
> 要展開中的下列非終端[語彙慣例](../cpp/lexical-conventions.md)一節*c + + 語言參考*:*常數*，*常數運算式*，*識別項*，*關鍵字*，*運算子*，並*標點符號*。

## <a name="see-also"></a>另請參閱

[文法摘要 (C/C++)](../preprocessor/grammar-summary-c-cpp.md)