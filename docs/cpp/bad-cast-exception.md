---
title: "bad_cast 例外狀況 | Microsoft Docs"
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
  - "bad_cast"
  - "bad_cast_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bad_cast 關鍵字 [C++]"
  - "例外狀況, bad_cast"
ms.assetid: 31eae1e7-d8d5-40a0-9fef-64a6a4fc9021
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# bad_cast 例外狀況
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若轉型為參考類型失敗，則 `dynamic_cast` 運算子會擲回 `bad_cast` 例外狀況。  
  
## 語法  
  
```  
catch (bad_cast)  
   statement  
```  
  
## 備註  
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
  
 擲回例外狀況是因為所轉型的物件 \(圖形\) 不是衍生自指定的轉換類型 \(圓形\)。  若要避免例外狀況，請將這些宣告加入至 `main`：  
  
```  
Circle circle_instance;  
Circle& ref_circle = circle_instance;  
```  
  
 然後在 `try` 區塊中反向轉型的意義，如下所示：  
  
```  
Shape& ref_shape = dynamic_cast<Shape&>(ref_circle);  
```  
  
## 請參閱  
 [dynamic\_cast 運算子](../cpp/dynamic-cast-operator.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)   
 [C\+\+ 例外狀況處理](../cpp/cpp-exception-handling.md)