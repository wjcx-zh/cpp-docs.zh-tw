---
title: "class (C++) | Microsoft Docs"
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
  - "class_cpp"
  - "class"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "class 關鍵字 [C++]"
  - "class 類型, class 陳述式"
ms.assetid: dd23c09f-6598-4069-8bff-69c7f2518b9f
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# class (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`class` 關鍵字宣告類別型別或定義類別型別的物件。  
  
## 語法  
  
```  
  
      [template-spec]  
       class [ms-decl-spec] [tag [: base-list ]]  
{  
   member-list  
} [declarators];  
[ class ] tag declarators;  
```  
  
#### 參數  
 `template-spec`  
 選擇性樣板規格。  如需詳細資訊，請參閱 [樣板規格](../Topic/Template%20Specifications.md)。  
  
 `class`  
 `class` 關鍵字。  
  
 `ms-decl-spec`  
 選擇性儲存類別規格。  如需詳細資訊，請參閱 [\_\_declspec](../cpp/declspec.md) 關鍵字。  
  
 `tag`  
 提供給類別的類型名稱。  標記會在類別的範圍內成為保留字。  標記是選擇性的。  如果省略，則會定義匿名類別。  如需詳細資訊，請參閱[匿名類別類型](../cpp/anonymous-class-types.md)。  
  
 `base-list`  
 將衍生此結構之成員的類別或類別的選擇性清單。  如需詳細資訊，請參閱 [基底類別](../cpp/base-classes.md)。  每一個基底類別或結構名稱前面可以有存取規範 \([public](../cpp/public-cpp.md)、[private](../cpp/private-cpp.md)、[protected](../cpp/protected-cpp.md)\) 和 [virtual](../cpp/virtual-cpp.md) 關鍵字。  如需詳細資訊，請參閱[控制類別成員的存取](../misc/controlling-access-to-class-members.md)。  
  
 `member-list`  
 類別成員的清單。  如需詳細資訊，請參閱[類別成員概觀](../cpp/class-member-overview.md)。  
  
 `declarators`  
 指定一個或多個執行個體名稱的類別型別來宣告子清單。  如果類別的所有資料成員都是 `public`，宣告子可能包含初始設定式清單。  在結構中根據預設資料成員是 `public` ，比在類別中常見。  如需詳細資訊，請參閱 [宣告子概觀](../cpp/overview-of-declarators.md)。  
  
## 備註  
 一般來說，如需類別的詳細資訊，請參閱下列其中一個主題:  
  
-   [struct](../cpp/struct-cpp.md)  
  
-   [union](../cpp/unions.md)  
  
-   [\_\_multiple\_inheritance](../cpp/inheritance-keywords.md)  
  
-   [\_\_single\_inheritance](../cpp/inheritance-keywords.md)  
  
-   [\_\_virtual\_inheritance](../cpp/inheritance-keywords.md)  
  
 如需 Managed 類別和結構的詳細資訊，請參閱[類別和結構](../windows/classes-and-structs-cpp-component-extensions.md)。  
  
## 範例  
  
```  
// class.cpp  
// compile with: /EHsc  
// Example of the class keyword  
// Exhibits polymorphism/virtual functions.  
  
#include <iostream>  
#include <string>  
#define TRUE = 1  
using namespace std;  
  
class dog  
{  
public:  
   dog()  
   {  
      _legs = 4;  
      _bark = true;  
   }  
  
   void setDogSize(string dogSize)  
   {  
      _dogSize = dogSize;  
   }  
   virtual void setEars(string type)      // virtual function  
   {  
      _earType = type;  
   }  
  
private:  
   string _dogSize, _earType;  
   int _legs;  
   bool _bark;  
  
};  
  
class breed : public dog  
{  
public:  
   breed( string color, string size)  
   {  
      _color = color;  
      setDogSize(size);  
   }  
  
   string getColor()  
   {  
      return _color;  
   }  
  
   // virtual function redefined  
   void setEars(string length, string type)  
   {  
      _earLength = length;  
      _earType = type;  
   }  
  
protected:  
   string _color, _earLength, _earType;  
};  
  
int main()  
{  
   dog mongrel;  
   breed labrador("yellow", "large");  
   mongrel.setEars("pointy");  
   labrador.setEars("long", "floppy");  
   cout << "Cody is a " << labrador.getColor() << " labrador" << endl;  
}  
```  
  
## 請參閱  
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)   
 [類別和結構](../cpp/classes-and-structs-cpp.md)