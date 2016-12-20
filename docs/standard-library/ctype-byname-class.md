---
title: "ctype_byname 類別 | Microsoft Docs"
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
  - "xlocale/std::ctype_byname"
  - "std::ctype_byname"
  - "ctype_byname"
  - "std.ctype_byname"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ctype_byname 類別"
ms.assetid: a5cec021-a1f8-425f-8757-08e6f064b604
caps.latest.revision: 22
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ctype_byname 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

衍生的範本類別描述可以做為特定地區設定 ctype Facet，啟用字元分類和呈現在情況的和原生和地區設定指定的字元集的物件。  
  
## 語法  
  
```  
template<class _Elem>  
class ctype_byname : public ctype<_Elem>  
{  
public:  
    explicit ctype_byname(  
        const char *_Locname,  
        size_t _Refs = 0  
    );  
    explicit ctype_byname(  
        const string& _Locname,  
        size_t _Refs = 0  
    );  
protected:  
    virtual __CLR_OR_THIS_CALL ~ctype_byname();  
};  
```  
  
## 備註  
 具名地區設定取決於其行為 `_Locname`。  每個建構函式並使用 [ctype](../standard-library/ctype-class.md)\<CharType\>\(`_Refs`\) 或對等的基礎物件基底類別的 `ctype<char>`。  
  
## 需求  
 **標題:** \<地區設定\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)