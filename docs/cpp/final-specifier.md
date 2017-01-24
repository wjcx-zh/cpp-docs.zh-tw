---
title: "final 規範 | Microsoft Docs"
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
  - "final"
  - "final_CPP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "final 識別項"
ms.assetid: 649866d0-79d4-449f-ab74-f84b911b79a3
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# final 規範
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以使用 `final` 關鍵字指定無法在衍生類別中覆寫的虛擬函式。  您也可以用它來指定無法被繼承的類別。  
  
## 語法  
  
```  
  
function-declaration final;  
```  
  
```  
  
class class-name final base-classes  
```  
  
## 備註  
 `final` 具有內容相關性，而且只有在函式宣告或類別名稱之後使用時才具有特殊意義，否則它不是保留的關鍵字。  
  
 當 `final` 用於類別宣告時，`base-classes` 是宣告中的選擇性部分。  
  
## 範例  
 下列範例會使用 `final` 關鍵字來指定無法覆寫的虛擬函式。  
  
```cpp  
class BaseClass  
{  
    virtual void func() final;  
};  
  
class DerivedClass: public BaseClass  
{  
    virtual void func(); // compiler error: attempting to   
                         // override a final function  
};  
```  
  
 如需如何指定可覆寫之成員函式的詳細資訊，請參閱[override 規範](../cpp/override-specifier.md)。  
  
 下一個範例會使用 `final` 關鍵字來指定無法被繼承的類別。  
  
```cpp  
class BaseClass final   
{  
};  
  
class DerivedClass: public BaseClass // compiler error: BaseClass is   
                                     // marked as non-inheritable  
{  
};  
```  
  
## 請參閱  
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)   
 [\(NOTINBUILD\) C\+\+ Type Names](http://msdn.microsoft.com/zh-tw/b53ba470-e583-4e5c-b634-6018f6110674)   
 [override 規範](../cpp/override-specifier.md)