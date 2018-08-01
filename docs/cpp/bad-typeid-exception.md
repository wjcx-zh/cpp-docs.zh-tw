---
title: bad_typeid 例外狀況 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- bad_typeid
- bad_typeid_cpp
dev_langs:
- C++
helpviewer_keywords:
- bad_typeid exception
- exceptions [C++], bad_typeid
ms.assetid: 5963ed58-4ede-4597-957d-f7bbd06299c2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 55718522bdbf618fb656eedc5c6afd59bfcaca08
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2018
ms.locfileid: "39409003"
---
# <a name="badtypeid-exception"></a>bad_typeid 例外狀況
**Bad_typeid**所擲回例外狀況[typeid 運算子](../cpp/typeid-operator.md)時的運算元**typeid**為 NULL 指標。  
  
## <a name="syntax"></a>語法  
  
```  
catch (bad_typeid)  
   statement  
```  
  
## <a name="remarks"></a>備註  
 介面**bad_typeid**是：  
  
```cpp 
class bad_typeid : public exception  
{  
public:  
   bad_typeid(const char * _Message = "bad typeid");  
   bad_typeid(const bad_typeid &);  
   virtual ~bad_typeid();  
};  
```  
  
 下列範例所示**typeid**擲回運算子**bad_typeid**例外狀況。  
  
```cpp 
// expre_bad_typeid.cpp  
// compile with: /EHsc /GR  
#include <typeinfo.h>  
#include <iostream>  
  
class A{  
public:  
   // object for class needs vtable  
   // for RTTI  
   virtual ~A();  
};  
  
using namespace std;  
int main() {  
A* a = NULL;  
  
try {  
   cout << typeid(*a).name() << endl;  // Error condition  
   }  
catch (bad_typeid){  
   cout << "Object is NULL" << endl;  
   }  
}  
```  
  
## <a name="output"></a>輸出  
  
```Output 
Object is NULL  
```  
  
## <a name="see-also"></a>另請參閱  
 [執行階段類型資訊](../cpp/run-time-type-information.md)   
 [關鍵字](../cpp/keywords-cpp.md)