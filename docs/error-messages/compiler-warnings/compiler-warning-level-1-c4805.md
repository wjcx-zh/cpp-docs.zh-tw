---
title: 編譯器警告 （層級 1） C4805 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4805
dev_langs:
- C++
helpviewer_keywords:
- C4805
ms.assetid: 99c7b7e2-272e-4ab5-8580-17c42e62e2ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 13477b20a046741e845c84fd1812dbc6c547ccbd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33281560"
---
# <a name="compiler-warning-level-1-c4805"></a>編譯器警告 (層級 1) C4805
'operation'：作業中不安全的混用類型 'type' 和類型 'type'  
  
 進行 [bool](../../cpp/bool-cpp.md) 和 [int](../../c-language/integer-types.md)之間的比較作業時會產生此警告。下列範例會產生 C4805：  
  
```  
// C4805.cpp  
// compile with: /W1  
int main() {  
   int i = 1;  
   bool b = true;  
  
   if (i == b) {   // C4805, comparing bool and int variables  
   }  
}  
```