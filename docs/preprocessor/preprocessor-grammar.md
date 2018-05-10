---
title: 前置處理器文法 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: d14a3e00e18a2d3ac69dd472ac4056a379ada224
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="preprocessor-grammar"></a>前置處理器文法
**#define***識別碼**語彙基元字串*選擇加入    
  
 *#* **定義***識別碼*[**(** *識別碼*選擇**，** *...* **，** *識別碼*選擇 **)**]*語彙基元字串*選擇加入    
  
 **defined(**  *identifier* **)**  
  
 **定義***識別碼*   
  
 `#include` **「***路徑規格***"**  
  
 `#include` **\<***路徑規格***>**  
  
 **#line**  *digit-sequence*  **"** *filename* **"** opt  
  
 *#* **undef***識別碼*   
  
 **#error***語彙基元字串*   
  
 **#pragma***語彙基元字串*   
  
 *條件式*:  
 *如果部分 elif 部分*選擇*else 部分*選擇*endif 列*  
  
 *如果部分*:  
 *if-linetext*  
  
 *如果行*:  
 **#if**  *constant-expression*  
  
 **#ifdef***識別碼*   
  
 **#ifndef***識別碼*   
  
 *elif 部分*:  
 *elif 行文字*  
  
 *elif 部分 elif 行文字*  
  
 *elif 列*:  
 **#elif**  *constant-expression*  
  
 *else 部分*:  
 *else-linetext*  
  
 *其他列*:  
 `#else`  
  
 *endif 列*:  
 `#endif`  
  
 *數字順序*:  
 *digit*  
  
 *digit-sequence digit*  
  
 *數字*： 其中一個  
 **0 1 2 3 4 5 6 7 8 9**  
  
 *語彙基元字串*:  
 語彙基元字串  
  
 *語彙基元*:  
 *keyword*  
  
 *identifier*  
  
 *constant*  
  
 *operator*  
  
 `punctuator`  
  
 *檔名*:  
 合法的作業系統檔名  
  
 *路徑規格*:  
 合法的檔案路徑  
  
 *文字*:  
 文字的任意序列  
  
> [!NOTE]
>  下列非終端項中擴充[語彙慣例](../cpp/lexical-conventions.md)區段*c + + 語言參考*: `constant`， `constant` -*運算式*，*識別碼*，*關鍵字*， `operator`，和`punctuator`。  
  
## <a name="see-also"></a>另請參閱  
 [文法摘要 (C/C++)](../preprocessor/grammar-summary-c-cpp.md)