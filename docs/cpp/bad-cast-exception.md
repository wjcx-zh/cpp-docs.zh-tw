---
title: bad_cast 例外狀況 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b50995ff1d5eb730bf6593679194d32d5300b9d7
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942624"
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
  
```cpp 
class bad_cast : public exception {  
public:  
   bad_cast(const char * _Message = "bad cast");  
   bad_cast(const bad_cast &);  
   virtual ~bad_cast();  
};  
```  
  
 下列程式碼範例包含失敗的 `dynamic_cast`，會擲回 `bad_cast` 例外狀況。  
  
```cpp 
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
  
 擲回例外狀況是因為所轉型的物件 (圖形) 不是衍生自指定的轉換類型 (圓形)。 若要避免例外狀況，這些將宣告加入至**主要**:  
  
```cpp 
Circle circle_instance;  
Circle& ref_circle = circle_instance;  
```  
  
 再反向轉換中的意義**嘗試**封鎖，如下所示：  
  
```cpp 
Shape& ref_shape = dynamic_cast<Shape&>(ref_circle);  
```  
  
## <a name="see-also"></a>另請參閱  
 [dynamic_cast 運算子](../cpp/dynamic-cast-operator.md)   
 [關鍵字](../cpp/keywords-cpp.md)   
 [C++ 例外狀況處理](../cpp/cpp-exception-handling.md)