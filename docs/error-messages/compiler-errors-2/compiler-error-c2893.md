---
title: "編譯器錯誤 C2893 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2893
dev_langs: C++
helpviewer_keywords: C2893
ms.assetid: ec0cbe43-005d-45da-8742-aaeb9b81d28e
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d6a926b6cf935d1910681b77d95f60847205bc05
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2893"></a>編譯器錯誤 C2893
無法特製化函式樣板 '範本名稱'  
  
 編譯器無法特製化函式樣板。 可以有許多原因造成此錯誤。  
  
 一般情況下，若要解決 C2893 錯誤的方式是檢閱函式的簽章，並請確定您可以具現化每個型別。  
  
## <a name="example"></a>範例  
 C2893 發生是因為`f`的樣板參數`T`推算出是`std::map<int,int>`，但`std::map<int,int>`沒有成員`data_type`(`T::data_type`不具現化與`T = std::map<int,int>`。)。 下列範例會產生 C2893。  
  
```  
// C2893.cpp  
// compile with: /c /EHsc  
#include<map>  
using namespace std;  
class MyClass {};  
  
template<class T>   
inline typename T::data_type  
// try the following line instead  
// inline typename  T::mapped_type  
f(T const& p1, MyClass const& p2);  
  
template<class T>  
void bar(T const& p1) {  
    MyClass r;  
    f(p1,r);   // C2893  
}  
  
int main() {  
   map<int,int> m;  
   bar(m);  
}  
```