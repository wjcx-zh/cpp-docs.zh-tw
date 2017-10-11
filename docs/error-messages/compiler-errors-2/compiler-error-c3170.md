---
title: "編譯器錯誤 C3170 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3170
dev_langs:
- C++
helpviewer_keywords:
- C3170
ms.assetid: ca9a59d6-7df3-42f0-b028-c09d0af3ac2a
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: aa11ac93ab7e5637153a063a892d99e127b80f54
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3170"></a>編譯器錯誤 C3170
無法在專案中有不同的模組識別項  
  
 [模組](../../windows/module-cpp.md)兩個在編譯檔案中找不到具有不同名稱的屬性。 只有一個唯一`module`屬性可以指定每個編譯。  
  
 相同`module`屬性都可以指定多個原始程式碼檔中。  
  
 例如，如果找不到下列的模組屬性：  
  
```  
// C3170.cpp  
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];  
int main() {}  
```  
  
 然後，  
  
```  
// C3170b.cpp  
// compile with: C3170.cpp  
// C3170 expected  
[ module(name="MyModule1", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];  
```  
  
 編譯器會產生 C3170 （請注意不同的名稱）。
