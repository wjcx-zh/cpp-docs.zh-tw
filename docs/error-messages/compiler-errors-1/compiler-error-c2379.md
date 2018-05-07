---
title: 編譯器錯誤 C2379 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2379
dev_langs:
- C++
helpviewer_keywords:
- C2379
ms.assetid: 37dc3015-a4af-4341-bbf3-da6150df7e51
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a1016bedfa9df0e9dfacb56734ee60397108d046
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2379"></a>編譯器錯誤 C2379
型式參數數目有不同的類型，當升級  
  
 指定參數的型別不相容，透過預設升級後，與上一個宣告中的類型。 這是 ANSI C 中的錯誤 ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) 和具有 Microsoft 擴充功能的警告 (**/Ze**)。  
  
 下列範例會產生 C2379:  
  
```  
// C2379.c  
// compile with: /Za  
void func();  
void func(char);   // C2379, char promotes to int  
```