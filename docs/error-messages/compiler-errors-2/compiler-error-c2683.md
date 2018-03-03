---
title: "編譯器錯誤 C2683 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2683
dev_langs:
- C++
helpviewer_keywords:
- C2683
ms.assetid: db605e4f-601b-4d05-92a1-c43ca24de08d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b02f157fbbb2e5b3e271f5df0803ece6ef0585a9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2683"></a>編譯器錯誤 C2683
'cast': 'type' 不是多型類型  
  
 您無法使用[dynamic_cast](../../cpp/dynamic-cast-operator.md)轉換非多型類別 （沒有虛擬函式的類別）。  
  
 您可以使用[static_cast](../../cpp/static-cast-operator.md)執行非多型類型的轉換。 不過，`static_cast`不會執行執行階段檢查。  
  
 下列範例會產生 C2683:  
  
```  
// C2683.cpp  
// compile with: /c  
class B { };  
class D : public B { };  
  
void f(B* pb) {  
   D* pd1 = dynamic_cast<D*>(pb);  // C2683  
   D* pd1 = static_cast<D*>(pb);   // OK  
}  
```