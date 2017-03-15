---
title: "codecvt_byname 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.codecvt_byname"
  - "codecvt_byname"
  - "std::codecvt_byname"
  - "xlocale/std::codecvt_byname"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "codecvt_byname 類別"
ms.assetid: b63b6c04-f60c-47b9-8e30-a933f24a8ffb
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# codecvt_byname 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述物件可以做為特定地區設定的定序 Facet 的衍生的樣板類別，啟用特定資訊擷取有關轉換的文化特性區域。  
  
## 語法  
  
```  
template<Class CharType, class Byte, class StateType>  
    class codecvt_byname: public codecvt<CharType, Byte, StateType> {  
public:  
    explicit codecvt_byname(  
        const char* _Locname,  
        size_t _Refs = 0  
    );  
```  
  
```  
explicit codecvt_byname(  
    const string& _Locname,  
    size_t _Refs = 0  
);  
```  
  
```  
protected:  
    virtual ~codecvt_byname( );  
};  
```  
  
#### 參數  
 `_Locname`  
 名為的地區設定。  
  
 `_Refs`  
 初始參考計數。  
  
## 備註  
 當具名地區設定時， Byname Facet 會自動建立。  
  
 具名地區設定取決於其行為 `_Locname`。  每個建構函式並使用 [codecvt](../standard-library/codecvt-class.md)\<CharType， Byte， StateType\>\(`_Refs`\) 的基礎物件。  
  
## 需求  
 **標題:** \<地區設定\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)