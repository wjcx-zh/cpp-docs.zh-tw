---
title: 編譯器錯誤 C2191 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2191
dev_langs:
- C++
helpviewer_keywords:
- C2191
ms.assetid: 051b8350-e5de-4f51-ab6e-96d32366bcef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aa4b590b494355450909032c78822553004beddc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2191"></a>編譯器錯誤 C2191
第二個參數清單比第一個長  
  
 C 函式宣告的第二個時間較長的參數清單。 C 不支援多載函式。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2191:  
  
```  
// C2191.c  
// compile with: /Za /c  
void func( int );  
void func( int, float );   // C2191 different parameter list  
void func2( int, float );   // OK  
```