---
title: "time_get_byname 類別 | Microsoft Docs"
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
  - "std.time_get_byname"
  - "time_get_byname"
  - "xloctime/std::time_get_byname"
  - "std::time_get_byname"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "time_get_byname 類別"
ms.assetid: 6e54153e-da40-4bb9-a942-1a6ce57b30c9
caps.latest.revision: 25
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# time_get_byname 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

衍生的範本類別描述可做為地區設定型別 `time_get`\<CharType， InputIterator\>Facet 的物件。  
  
## 語法  
  
```  
template<class Elem, class InputIterator =   
   istreambuf_iterator<CharType, char_traits<CharType> > >  
   class time_get_byname : public time_get<CharType, InputIterator>  
{  
public:  
    explicit time_get_byname(  
        const char *_Locname,  
         size_t _Refs = 0  
    );  
    explicit time_get_byname(  
        const string& _Locname,  
        size_t _Refs = 0  
    );  
protected:  
    virtual ~time_get_byname()  
};  
```  
  
#### 參數  
 `_Locname`  
 名為的地區設定。  
  
 `_Refs`  
 初始參考計數。  
  
## 需求  
 具名地區設定取決於其行為 `_Locname`。  每個建構函式並使用 [time\_get](../Topic/time_get::time_get.md)\<， CharType InputIterator\>\(`_Refs`\) 的基礎物件。  
  
## 需求  
 **標題:** \<地區設定\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)