---
title: 編譯器錯誤 C3170 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3170
dev_langs:
- C++
helpviewer_keywords:
- C3170
ms.assetid: ca9a59d6-7df3-42f0-b028-c09d0af3ac2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8bb077bcad95de0be17e630803b5d4ea9825be61
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33255909"
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