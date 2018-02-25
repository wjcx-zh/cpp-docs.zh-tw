---
title: "#ifdef 和 #ifndef 指示詞 （C/c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- '#ifndef'
- '#ifdef'
dev_langs:
- C++
helpviewer_keywords:
- '#ifdef directive'
- preprocessor, directives
- ifdef directive (#ifdef)
- ifndef directive (#ifndef)
- '#ifndef directive'
ms.assetid: 2b0be69d-9e72-45d8-8e24-e4130fb2455b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a8f1a10e9d8437b71591efc9ce2915c9f485e0c4
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="ifdef-and-ifndef-directives-cc"></a>#ifdef 和 #ifndef 指示詞 (C/C++)
**#Ifdef**和**#ifndef**指示詞會執行相同的工作`#if`指示詞搭配使用時**定義**( *的識別項* ).  
  
## <a name="syntax"></a>語法  
  
```  
#ifdef identifier  
#ifndef identifier  
  
// equivalent to  
#if defined identifier  
#if !defined identifier  
```  
  
## <a name="remarks"></a>備註  
 您可以使用**#ifdef**和**#ifndef**任何位置的指示詞`#if`可用。 **#Ifdef** *識別碼*陳述式相當於`#if 1`時*識別碼*已定義，而且它相當於`#if 0`時*識別碼*未定義或有已具有未定義`#undef`指示詞。 這些指示詞只會檢查 `#define` 所定義的識別項是否存在，不適用於 C 或 C++ 原始程式碼中宣告的識別項。  
  
 提供這些指示詞的目的只是為了保留與舊版語言的相容性。 **定義 (** *識別碼* **)**常數運算式搭配`#if`指示詞。  
  
 **#Ifndef**指示詞會檢查所檢查的條件相反**#ifdef**。 如果尚未定義識別項 (或是已使用 `#undef` 移除其定義)，則條件為 true (非零)。 否則，條件為 false (0)。  
  
 **Microsoft 特定的**  
  
 *識別碼*可以從命令列使用 /D 選項傳遞。 使用 /D 最多可以指定 30 個巨集。  
  
 這個選項在檢查定義是否存在時很實用，因為可以從命令列傳遞定義。 例如:   
  
```  
// ifdef_ifndef.CPP  
// compile with: /Dtest /c  
#ifndef test  
#define final  
#endif  
```  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [前置處理器指示詞](../preprocessor/preprocessor-directives.md)