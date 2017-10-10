---
title: "編譯器錯誤 C2632 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2632
dev_langs:
- C++
helpviewer_keywords:
- C2632
ms.assetid: b15a6b1b-42d2-4e1b-8660-e6bfde61052d
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: c1af198d4949da112792c2bbddfac68a80d0daf4
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2632"></a>編譯器錯誤 C2632
'type1' 後面接著 'type2' 是不合法  
  
 如果遺漏之間兩個型別規範中的程式碼，可能造成這個錯誤。  
  
 下列範例會產生 C2632:  
  
```  
// C2632.cpp  
int float i;   // C2632  
```  
  
 也可以針對 Visual Studio.NET 2003年所進行的編譯器一致性工作產生這個錯誤。 `bool`現在是適當的型別。 在舊版中， `bool` typedef，且您可以建立具有該名稱的識別項。  
  
 下列範例會產生 C2632:  
  
```  
// C2632_2.cpp  
// compile with: /LD  
void f(int bool);   // C2632  
```  
  
 若要解決這個錯誤，以便程式碼是有效的 Visual c + + 的 Visual Studio.NET 2003年和 Visual Studio.NET 版本中，重新命名識別項。
