---
title: 編譯器警告 C4950 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4950
dev_langs:
- C++
helpviewer_keywords:
- C4950
ms.assetid: 50226a5c-c664-4d09-ac59-e9e874ca244f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 55221cc233c74e612dd4a521641be90a6dbf9314
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-c4950"></a>編譯器警告 C4950
'type_or_member' : 標記為過時  
  
成員或類型已標記為過時<xref:System.ObsoleteAttribute>屬性。  
  
C4950 一律發出為錯誤。 您可以關閉此警告使用[警告](../../preprocessor/warning.md)pragma 指示詞或[/wd](../../build/reference/compiler-option-warning-level.md)編譯器選項。  
  
## <a name="example"></a>範例  
下列範例會產生 C4950：  
  
```cpp  
// C4950.cpp  
// compile with: /clr  
using namespace System;  
  
// Any reference to Func3 should generate an error with message  
[System::ObsoleteAttribute("Will be removed in next version", true)]  
Int32 Func3(Int32 a, Int32 b) {  
   return (a + b);  
}  
  
int main() {  
   Int32 MyInt3 = ::Func3(2, 2);   // C4950  
}  
```