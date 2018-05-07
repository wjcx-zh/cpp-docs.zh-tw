---
title: 編譯器錯誤 C3842 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3842
dev_langs:
- C++
helpviewer_keywords:
- C3842
ms.assetid: 41a1a44a-c618-40a2-8d26-7da27d14095d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c29878f7d64bfe1ed444130c77461dece6d20302
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3842"></a>編譯器錯誤 C3842
'function'：不支援 WinRT 或 Managed 類型的成員函式上的 'const' 和 'volatile' 限定詞  
  
 [const](../../cpp/const-cpp.md)和[volatile](../../cpp/volatile-cpp.md)不支援 Windows 執行階段或 managed 的類型的成員函式。  
  
 下列範例會產生 C3842：  
  
```  
// C3842a.cpp  
// compile with: /clr /c  
public ref struct A {  
   void f() const {}   // C3842  
   void f() volatile {}   // C3842  
  
   void f() {}  
};  
```