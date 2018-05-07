---
title: 編譯器錯誤 C2356 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2356
dev_langs:
- C++
helpviewer_keywords:
- C2356
ms.assetid: 84d5a816-9a61-4d45-9978-38e485bbf767
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a9dfb13f388c6c40c6c1853ab8e87b2e39edbc1e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2356"></a>編譯器錯誤 C2356
在轉譯單位不得變更初始化區段  
  
 可能的原因：  
  
-   `#pragma init_seg` 加上區段初始化程式碼  
  
-   `#pragma init_seg` 加上另一個 `#pragma init_seg`  
  
 若要解決，將移至模組開頭的區段初始化程式碼。 如果必須初始化多個區域，將其移到個別的模組。  
  
 下列範例會產生 C2356:  
  
```  
// C2356.cpp  
#pragma warning(disable : 4075)  
  
int __cdecl myexit(void (__cdecl *)());  
int __cdecl myexit2(void (__cdecl *)());  
  
#pragma init_seg(".mine$m",myexit)  
#pragma init_seg(".mine$m",myexit2)   // C2356  
```