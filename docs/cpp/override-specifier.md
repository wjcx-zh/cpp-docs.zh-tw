---
title: "override 規範 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "override 識別項"
ms.assetid: b286fb46-9374-4ad8-b2e7-4607119b6133
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# override 規範
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以使用 `override` 關鍵字指定可覆寫基底類別中之虛擬函式的成員函式。  
  
## 語法  
  
```  
  
function-declaration override;  
```  
  
## 備註  
 `override` 具有內容相關性，而且只有在成員函式宣告之後使用時才具有特殊意義，否則不是保留的關鍵字。  
  
## 範例  
 使用 `override` 有助於防止程式碼中發生意外的繼承行為。  下列範例將示範在不使用 `override` 的情況下，衍生類別可能產生的非預期成員函式行為。  編譯器不會對這個程式碼發出任何錯誤。  
  
```cpp  
class BaseClass  
{  
    virtual void funcA();  
    virtual void funcB() const;  
    virtual void funcC(int = 0);  
    void funcD();  
};  
  
class DerivedClass: public BaseClass  
{  
    virtual void funcA(); // ok, works as intended  
  
    virtual void funcB(); // DerivedClass::funcB() is non-const, so it does not  
                          // override BaseClass::funcB() const and it is a new member function  
  
    virtual void funcC(double = 0.0); // DerivedClass::funcC(double) has a different  
                                      // parameter type than BaseClass::funcC(int), so  
                                      // DerivedClass::funcC(double) is a new member function  
  
};  
  
```  
  
 當您使用 `override` 時，編譯器會產生錯誤，而不是以無訊息方式建立新的成員函式。  
  
```cpp  
class BaseClass  
{  
    virtual void funcA();  
    virtual void funcB() const;  
    virtual void funcC(int = 0);  
    void funcD();  
};  
  
class DerivedClass: public BaseClass  
{  
    virtual void funcA() override; // ok  
  
    virtual void funcB() override; // compiler error: DerivedClass::funcB() does not   
                                   // override BaseClass::funcB() const  
  
    virtual void funcC( double = 0.0 ) override; // compiler error:   
                                                 // DerivedClass::funcC(double) does not   
                                                 // override BaseClass::funcC(int)  
  
    void funcD() override; // compiler error: DerivedClass::funcD() does not   
                           // override the non-virtual BaseClass::funcD()  
};  
  
```  
  
 若要指定無法覆寫函式且無法繼承類別，請使用 [final](../cpp/final-specifier.md) 關鍵字。  
  
## 請參閱  
 [final 規範](../cpp/final-specifier.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)   
 [\(NOTINBUILD\) C\+\+ Type Names](http://msdn.microsoft.com/zh-tw/b53ba470-e583-4e5c-b634-6018f6110674)