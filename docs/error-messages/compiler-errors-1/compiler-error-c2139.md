---
title: 編譯器錯誤 C2139 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2139
dev_langs:
- C++
helpviewer_keywords:
- C2139
ms.assetid: 31e047c0-5bf9-46c2-b6de-b627ea6a5768
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dd56ee920d3f53b22d9979b45c39fa78b9054662
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33169800"
---
# <a name="compiler-error-c2139"></a>編譯器錯誤 C2139
'type': 未定義的類別不允許做為編譯器內建類型特性 '特性' 的引數  
  
 無效的引數傳遞給類型特性。  
  
 如需詳細資訊，請參閱[類型特性的編譯器支援](../../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2139。  
  
```  
// C2139.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
template <class T>  
struct is_polymorphic {  
   static const bool value = __is_polymorphic(T);  
};  
  
class C;  
class D {};  
  
class E {  
public:  
   virtual void Test() {}  
};  
  
int main() {  
   cout << is_polymorphic<C>::value << endl;   // C2139  
   cout << is_polymorphic<D>::value << endl;   // OK  
   cout << is_polymorphic<E>::value << endl;   // OK  
}  
```