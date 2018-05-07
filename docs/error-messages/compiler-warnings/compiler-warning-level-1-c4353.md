---
title: 編譯器警告 （層級 1） C4353 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4353
dev_langs:
- C++
helpviewer_keywords:
- C4353
ms.assetid: 6e79f186-ed82-4c95-9923-0ad5bb9c4db1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e7b9974635fabc07f17b9e46b16d163c72b6d3ea
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4353"></a>編譯器警告 (層級 1) C4353
使用非標準擴充： 常數 0 當做函式運算式。 請改用 '__noop' 函式內建函式  
  
 您無法使用常數零 (0) 做為函式運算式。 如需詳細資訊，請參閱[__noop](../../intrinsics/noop.md)。  
  
 下列範例會產生 C4353:  
  
```  
// C4353.cpp  
// compile with: /W1  
void MyPrintf(void){};  
#define X 0  
#if X  
   #define DBPRINT MyPrint  
#else  
   #define DBPRINT 0   // C4353 expected  
#endif  
int main(){  
DBPRINT();  
}  
```