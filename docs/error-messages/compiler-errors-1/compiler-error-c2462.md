---
title: 編譯器錯誤 C2462 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2462
dev_langs:
- C++
helpviewer_keywords:
- C2462
ms.assetid: a8601bf8-f5ce-41de-9117-e2632bd4996b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e4ce82ed15bdb8844f69abc260446c1af2fd4a0f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2462"></a>編譯器錯誤 C2462
'identifier': 無法在 'new-expression' 中定義的型別  
  
 您無法將類型定義的運算元欄位`new`運算子。 將型別定義放在個別的陳述式。  
  
 下列範例會產生 C2462:  
  
```  
// C2462.cpp  
int main() {  
   new struct S { int i; };   // C2462  
}  
```