---
title: 編譯器警告 （層級 4） C4510 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4510
dev_langs:
- C++
helpviewer_keywords:
- C4510
ms.assetid: fd28d1d4-ad27-4dad-94c0-9dba46c93180
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5b280a15381f53b6836b321e25717cbed19c7271
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4510"></a>編譯器警告 (層級 4) C4510
'class': 無法產生預設建構函式  
  
 建立沒有使用者定義建構函式和編譯器無法產生指定類別的預設建構函式。 您無法建立此類型的物件。  
  
 在幾種情況，會阻止編譯器產生的預設建構函式，包括：  
  
-   常數的資料成員。  
  
-   資料成員之參考。  
  
 您需要建立使用者定義的預設建構函式初始化這些成員的類別。  
  
 下列範例會產生 C4510:  
  
```  
// C4510.cpp  
// compile with: /W4  
struct A {  
   const int i;  
   int &j;  
   A& operator=( const A& ); // C4510 expected  
   // uncomment the following line to resolve this C4510  
   // A(int ii, int &jj) : i(ii), j(jj) {}  
};   // C4510  
  
int main() {  
}  
```