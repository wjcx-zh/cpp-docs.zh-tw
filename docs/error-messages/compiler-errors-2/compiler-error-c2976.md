---
title: 編譯器錯誤 C2976 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2976
dev_langs:
- C++
helpviewer_keywords:
- C2976
ms.assetid: d9bf9836-325e-4f72-a7e3-a67cf19d32e7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c2ff5fd23d02e835cfaa36b96ce75a1c74d16bd3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33244806"
---
# <a name="compiler-error-c2976"></a>編譯器錯誤 C2976
'identifier': 型別引數太少  
  
 泛型或樣板遺漏一個或多個實際引數。 請檢查泛型或樣板宣告，以找出正確的參數數目。  
  
 這個錯誤可能被因遺漏 c + + 標準程式庫元件中的樣板引數。  
  
 下列範例會產生 C2976:  
  
```  
// C2976.cpp  
template <class T>   
struct TC {  
   T t;  
};  
int main() {  
   TC<>* t;   // C2976  
   TC<int>* t2;   // OK  
}  
```  
  
 使用泛型時，也會發生 C2976:  
  
```  
// C2976b.cpp  
// compile with: /clr  
generic <class T>  
ref struct GC {  
   T t;  
};  
  
int main() {  
   GC<>^ g;   // C2976  
   GC<int>^ g2;   // OK  
}  
```