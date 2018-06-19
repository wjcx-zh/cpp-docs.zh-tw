---
title: 編譯器錯誤 C3172 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3172
dev_langs:
- C++
helpviewer_keywords:
- C3172
ms.assetid: 1834e2fd-6036-4c33-aff2-b51bc7c99441
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b3feadd9c8fc39edb707e8dbd3a80ed90d078d72
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33254372"
---
# <a name="compiler-error-c3172"></a>編譯器錯誤 C3172
'適於': 無法在專案中指定不同的 idl_module 屬性  
  
 [idl_module](../../windows/idl-module.md)屬性具有相同名稱但不同`dllname`或`version`兩個在編譯檔案中找不到參數。 只有一個唯一`idl_module`屬性可以指定每個編譯。  
  
 相同`idl_module`屬性都可以指定多個原始程式碼檔中。  
  
 例如，如果下列`idl_module`找不到屬性：  
  
```  
// C3172.cpp  
[module(name="MyMod")];  
[ idl_module(name="x", dllname="file.dll", version="1.1") ];  
int main() {}  
```  
  
 然後，  
  
```  
// C3172b.cpp  
// compile with: C3172.cpp  
// C3172 expected  
[ idl_module(name="x", dllname="file.dll", version="1.0") ];  
```  
  
 編譯器會產生 C3172 （請注意不同的版本值）。