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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ed053e37dfbf5f3c85cf1f8ec44912eca3148315
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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