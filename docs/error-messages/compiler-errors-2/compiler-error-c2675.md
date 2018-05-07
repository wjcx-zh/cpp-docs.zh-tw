---
title: 編譯器錯誤 C2675 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2675
dev_langs:
- C++
helpviewer_keywords:
- C2675
ms.assetid: 4b92a12b-bff8-4dd5-a109-620065fc146c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fb949f5d6ab5881b911bab89150ae13f47443fcf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2675"></a>編譯器錯誤 C2675
一元 'operator': '類型' 未定義此運算子或轉換為可接受的類型為預先定義的運算子  
  
 C2675 也可能使用一元運算子和類型未定義的運算子或轉換為可接受的類型給預先定義的操作員。 若要使用運算子，您必須針對指定類型進行多載，或針對已定義運算子的類型定義轉換。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2675。  
  
```  
// C2675.cpp  
struct C {   
   C(){}  
} c;  
  
struct D {   
   D(){}  
   void operator-(){}  
} d;  
  
int main() {  
   -c;   // C2675  
   -d;   // OK  
}  
```