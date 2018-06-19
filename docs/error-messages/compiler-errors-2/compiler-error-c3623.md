---
title: 編譯器錯誤 C3623 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3623
dev_langs:
- C++
helpviewer_keywords:
- C3623
ms.assetid: a0341b45-062a-4f67-beb9-ba74201ed1ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 231826dbcb38bb6bdae490c2f86954e1a56c2b77
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33254893"
---
# <a name="compiler-error-c3623"></a>編譯器錯誤 C3623
'variable': Managed 或 WinRT 型別中不支援位元欄位  
  
 在 Managed 或 WinRT 類別中的變數上不允許使用位元欄位。  
  
 下列範例會產生 C3623：  
  
```  
// C3623.cpp  
// compile with: /clr  
using namespace System;  
ref class CMyClass {  
public:  
   int i : 1;   // C3623  
};  
  
int main() {  
   CMyClass^ pMyClass = gcnew CMyClass();  
   pMyClass->i = 3;  
   Console::Out->WriteLine(pMyClass->i);  
}  
```  
