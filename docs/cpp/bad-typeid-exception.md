---
title: "bad_typeid 例外狀況 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "bad_typeid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bad_typeid 例外狀況"
  - "例外狀況, bad_typeid"
ms.assetid: 5963ed58-4ede-4597-957d-f7bbd06299c2
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# bad_typeid 例外狀況
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當 `typeid` 的運算元為 NULL 指標時，會由 [typeid 運算子](../cpp/typeid-operator.md)擲回 `bad_typeid` 例外狀況。  
  
## 語法  
  
```  
  
      catch (bad_typeid)  
   statement  
```  
  
## 備註  
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
  
 下列範例顯示擲回 `bad_typeid` 例外狀況的 `typeid`。  
  
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
  
## 輸出  
  
```  
Object is NULL  
```  
  
## 請參閱  
 [執行階段類型資訊](../cpp/run-time-type-information.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)