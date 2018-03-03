---
title: "編譯器錯誤 C2448 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2448
dev_langs:
- C++
helpviewer_keywords:
- C2448
ms.assetid: e255df3c-f861-4b4d-a193-8768cef061a5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cf628cb40be9c6f5dadf978983f86122a72f847f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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