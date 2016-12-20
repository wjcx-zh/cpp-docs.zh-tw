---
title: "moneypunct_byname 類別 | Microsoft Docs"
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
  - "std.moneypunct_byname"
  - "std::moneypunct_byname"
  - "xlocmon/std::moneypunct_byname"
  - "moneypunct_byname"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "moneypunct_byname 類別"
ms.assetid: e8a544d2-6aee-420d-b513-deb385c9b416
caps.latest.revision: 22
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# moneypunct_byname 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述物件可以做為特定地區設定 `moneypunct` Facet，啟用格式化貨幣輸入欄位或貨幣輸出欄位的衍生的範本類別。  
  
## 語法  
  
```  
template<class CharType, bool Intl = false>  
class moneypunct_byname : public moneypunct<CharType, Intl>  
{  
public:  
    explicit moneypunct_byname(  
        const char *_Locname,  
        size_t _Refs = 0  
    );  
    explicit moneypunct_byname(  
        const string& _Locname,  
        size_t _Refs = 0  
    );   
protected:  
    virtual ~moneypunct_byname();  
};  
```  
  
## 備註  
 具名地區設定取決於其行為 `_Locname`。  每個建構函式並使用 [moneypunct](../Topic/moneypunct::moneypunct.md)\<CharType， Intl\>\(`_Refs`\) 的基礎物件。  
  
## 需求  
 **標題:** \<地區設定\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)