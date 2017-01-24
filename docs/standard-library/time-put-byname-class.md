---
title: "time_put_byname 類別 | Microsoft Docs"
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
  - "time_put_byname"
  - "xloctime/std::time_put_byname"
  - "std.time_put_byname"
  - "std::time_put_byname"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "time_put_byname 類別"
ms.assetid: e08c2348-64d2-4ace-98b1-1496e14c7b1a
caps.latest.revision: 25
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# time_put_byname 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

衍生的樣板類別描述可以做為地區設定 facet 的型別物件 `time_put`\< CharType、 OutputIterator \>。  
  
## 語法  
  
```  
template<class CharType,  
 class OutIt = ostreambuf_iterator<CharType, char_traits<CharType> > >  
 class time_put_byname : public time_put<CharType, OutputIterator>  
{  
public:  
    explicit time_put_byname(  
        const char *_Locname,  
        size_t _Refs = 0  
    );  
    explicit time_put_byname(  
        const string& _Locname,  
        size_t _Refs = 0  
    );  
protected:  
    virtual ~time_put_byname();  
};  
```  
  
#### 參數  
 `_Locname`  
 地區設定名稱。  
  
 `_Refs`  
 初始的參考計數。  
  
## 備註  
 其行為取決於 [名為](../Topic/locale::name.md) 地區設定 `_Locname`。 每個建構函式初始化具有其基底物件 [time\_put](../Topic/time_put::time_put.md)\< CharType、 OutputIterator \> \(`_Refs`\)。  
  
## 需求  
 **標頭：**\<locale\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)