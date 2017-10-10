---
title: "編譯器錯誤 C2735 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2735
dev_langs:
- C++
helpviewer_keywords:
- C2735
ms.assetid: 6ce45600-7148-4bc0-8699-af0ef137571e
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 1008ef6178a4220bac718e08ba31a36d5db3242f
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2735"></a>編譯器錯誤 C2735
在型式參數類型規範中不允許 'keyword' 關鍵字  
  
 關鍵字在此內容中無效。  
  
 下列範例會產生 C2735:  
  
```  
// C2735.cpp  
void f(inline int){}   // C2735  
```
