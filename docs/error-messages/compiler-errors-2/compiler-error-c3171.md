---
title: "編譯器錯誤 C3171 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3171
dev_langs:
- C++
helpviewer_keywords:
- C3171
ms.assetid: 1ce26997-7ef1-4c9f-84da-003ea1a4251e
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: ebd64aa2c80f6e21b1e5c1829d8e165d46207718
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3171"></a>編譯器錯誤 C3171
'module': 無法在專案中指定不同的模組屬性  
  
 [模組](../../windows/module-cpp.md)兩個在編譯檔案中找不到具有不同的參數清單的屬性。 只有一個唯一`module`屬性可以指定每個編譯。  
  
 相同`module`屬性都可以指定多個原始程式碼檔中。  
  
 例如，如果下列`module`找不到屬性：  
  
```  
// C3171.cpp  
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.0") ];  
int main() {}  
```  
  
 然後，  
  
```  
// C3171b.cpp  
// compile with: C3171.cpp  
// C3171 expected  
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.1") ];  
```  
  
 編譯器會產生 C3171 （請注意不同的版本值）。
