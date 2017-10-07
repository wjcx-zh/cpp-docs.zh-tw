---
title: "bad_typeid 例外狀況 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
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
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: ea7dc85862622180038cf520ef92b752b65eba84
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="badtypeid-exception"></a>bad_typeid 例外狀況
`bad_typeid`所擲回例外狀況[typeid 運算子](../cpp/typeid-operator.md)時的運算元`typeid`為 NULL 指標。  
  
## <a name="syntax"></a>語法  
  
```  
  
      catch (bad_typeid)  
   statement  
```  
  
## <a name="remarks"></a>備註  
 `bad_typeid` 的介面為：  
  
```  
class bad_typeid : public exception  
{  
public:  
   bad_typeid(const char * _Message = "bad typeid");  
   bad_typeid(const bad_typeid &);  
   virtual ~bad_typeid();  
};  
```  
  
 下列範例顯示擲回 `typeid` 例外狀況的 `bad_typeid`。  
  
```  
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
  
```  
Object is NULL  
```  
  
## <a name="see-also"></a>另請參閱  
 [執行階段類型資訊](../cpp/run-time-type-information.md)   
 [關鍵字](../cpp/keywords-cpp.md)
