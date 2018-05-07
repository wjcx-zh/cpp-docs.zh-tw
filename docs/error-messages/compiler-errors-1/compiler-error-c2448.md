---
title: 編譯器錯誤 C2448 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2448
dev_langs:
- C++
helpviewer_keywords:
- C2448
ms.assetid: e255df3c-f861-4b4d-a193-8768cef061a5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bcc62d7aeba0a128c9b736586e6c1502227de717
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2448"></a>編譯器錯誤 C2448
'identifier': 函式樣式初始設定式似乎是函式定義  
  
 函式定義不正確。  
  
 這個錯誤可能被因舊式 C 語言的型式清單。  
  
 下列範例會產生 C2448:  
  
```  
// C2448.cpp  
void func(c)  
   int c;  
{}   // C2448  
```