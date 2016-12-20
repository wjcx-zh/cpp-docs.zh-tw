---
title: "basic_iostream 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "istream/std::basic_iostream"
  - "std.basic_iostream"
  - "basic_iostream"
  - "std::basic_iostream"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_iostream 類別"
ms.assetid: 294b680b-eb49-4066-8db2-6d52dac9d6e3
caps.latest.revision: 22
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# basic_iostream 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可執行輸入和輸出的資料流類別。  
  
## 語法  
  
```  
template <class Elem, class Tr = char_traits<Elem> >  
    class basic_iostream : public basic_istream<Elem, Tr>,  
        public basic_ostream<Elem, Tr>  
{  
public:  
    explicit basic_iostream(basic_streambuf<Elem, Tr> *_Strbuf);  
    virtual ~basic_iostream();  
};  
```  
  
## 備註  
 此範本類別描述透過其基底類別 [basic\_ostream](../standard-library/basic-ostream-class.md)\<`Elem`, `Tr`\> 控制插入的物件，和透過其基底類別 [basic\_istream](../standard-library/basic-istream-class.md)\<`Elem`, `Tr`\> 擷取的物件。  兩個物件共用通用的虛擬基底類別 [basic\_ios](../standard-library/basic-ios-class.md)\<`Elem`, `Tr`\>。  它們也會以 `Elem` 類型的項目 \(其字元特性由類別 `Tr` 決定\) 管理通用的資料流緩衝區。  此建構函式會藉由 `basic_istream`\(**strbuf**\) 和 `basic_ostream`\(**strbuf**\) 初始化其基底類別。  
  
### 建構函式  
  
|||  
|-|-|  
|[basic\_iostream](../Topic/basic_iostream::basic_iostream.md)|建立 `basic_iostream` 物件。|  
  
### 成員函式  
  
|||  
|-|-|  
|[交換](../Topic/basic_iostream::swap.md)|將提供之 `basic_iostream` 物件的內容與此物件的內容交換。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\=](../Topic/basic_iostream::operator=.md)|將指定的 `basic_iostream` 物件值指派給這個物件。  這是一個移動指派，涉及不會留下複本的 `rvalue`。|  
  
## 需求  
 **標頭：**\<istream\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostreams 慣例](../standard-library/iostreams-conventions.md)