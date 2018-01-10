---
title: "前置處理器文法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- preprocessor
- grammar, preprocessor
- preprocessor, grammar
ms.assetid: 6cd33fad-0b08-4592-9be8-7359c43e24e9
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 797d4bf4274a92ca4f265d01579698c0f9c6a4a3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="preprocessor-grammar"></a>前置處理器文法
**#define***識別碼**語彙基元字串*選擇加入    
  
 *#***定義***識別碼*[**(** *識別碼*選擇**，** *...* **，** *識別碼*選擇**)**]*語彙基元字串*選擇加入    
  
 **定義 (***識別碼* **)**   
  
 **定義***識別碼*   
  
 `#include`**"***路徑規格***"**  
  
 `#include` **\<** *路徑規格***>**  
  
 **#line***數字順序***"** *filename* **"**選擇加入      
  
 *#***undef***識別碼*   
  
 **#error***語彙基元字串*   
  
 **#pragma***語彙基元字串*   
  
 *條件式*:  
 *如果部分 elif 部分*選擇*else 部分*選擇*endif 列*  
  
 *如果部分*:  
 *如果 linetext*  
  
 *如果行*:  
 **#if***常數運算式*   
  
 **#ifdef***識別碼*   
  
 **#ifndef***識別碼*   
  
 *elif 部分*:  
 *elif 行文字*  
  
 *elif 部分 elif 行文字*  
  
 *elif 列*:  
 **#elif***常數運算式*   
  
 *else 部分*:  
 *其他 linetext*  
  
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
  
## <a name="see-also"></a>請參閱  
 [文法摘要 (C/C++)](../preprocessor/grammar-summary-c-cpp.md)