---
title: "bad_cast 例外狀況 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- bad_cast
- bad_cast_cpp
dev_langs:
- C++
helpviewer_keywords:
- exceptions [C++], bad_cast
- bad_cast keyword [C++]
ms.assetid: 31eae1e7-d8d5-40a0-9fef-64a6a4fc9021
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 70758ca099853f94ad06b8a9f5029203a480a772
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="badcast-exception"></a>bad_cast 例外狀況
若轉型為參考類型失敗，則 `bad_cast` 運算子會擲回 `dynamic_cast` 例外狀況。  
  
## <a name="syntax"></a>語法  
  
```  
catch (bad_cast)  
   statement  
```  
  
## <a name="remarks"></a>備註  
 `bad_cast` 的介面為：  
  
```  
class bad_cast : public exception {  
public:  
   bad_cast(const char * _Message = "bad cast");  
   bad_cast(const bad_cast &);  
   virtual ~bad_cast();  
};  
```  
  
 下列程式碼範例包含失敗的 `dynamic_cast`，會擲回 `bad_cast` 例外狀況。  
  
```  
// expre_bad_cast_Exception.cpp  
// compile with: /EHsc /GR  
#include <typeinfo.h>  
#include <iostream>  
  
class Shape {  
public:  
   virtual void virtualfunc() const {}  
};  
  
class Circle: public Shape {  
public:  
   virtual void virtualfunc() const {}  
};  
  
using namespace std;  
int main() {  
   Shape shape_instance;  
   Shape& ref_shape = shape_instance;  
   try {  
      Circle& ref_circle = dynamic_cast<Circle&>(ref_shape);   
   }  
   catch (bad_cast b) {  
      cout << "Caught: " << b.what();  
   }  
}  
```  
  
 擲回例外狀況是因為所轉型的物件 (圖形) 不是衍生自指定的轉換類型 (圓形)。 若要避免例外狀況，請將這些宣告加入至 `main`：  
  
```  
Circle circle_instance;  
Circle& ref_circle = circle_instance;  
```  
  
 然後在 `try` 區塊中反向轉型的意義，如下所示：  
  
```  
Shape& ref_shape = dynamic_cast<Shape&>(ref_circle);  
```  
  
## <a name="see-also"></a>另請參閱  
 [dynamic_cast 運算子](../cpp/dynamic-cast-operator.md)   
 [關鍵字](../cpp/keywords-cpp.md)   
 [C++ 例外狀況處理](../cpp/cpp-exception-handling.md)
