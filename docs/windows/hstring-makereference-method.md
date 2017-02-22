---
title: "HString::MakeReference 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HString::MakeReference"
dev_langs: 
  - "C++"
ms.assetid: 9e1fd2b2-66ad-4a50-b647-a20ab10e522f
caps.latest.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 2
---
# HString::MakeReference 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從指定的字串參數建立 HStringReference 物件。  
  
## 語法  
  
```  
template<unsigned int sizeDest>  
    static HStringReference MakeReference(  
              wchar_t const (&str)[ sizeDest]);  
  
    template<unsigned int sizeDest>  
    static HStringReference MakeReference(  
              wchar_t const (&str)[sizeDest],   
              unsigned int len);  
```  
  
#### 參數  
 `sizeDest`  
 指定目的 HStringReference 緩衝區大小的樣板參數。  
  
 `str`  
 寬字元字串的參考。  
  
 `len`  
 在這項作業使用的 `str` 參數緩衝區的最大長度。  如果 `len` 未指定參數，則會使用整個 `str` 參數。  
  
## 傳回值  
 值與指定的 `str` 參數相同的 HStringReference 物件。  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間：**Microsoft::WRL::Wrappers  
  
## 請參閱  
 [HString 類別](../windows/hstring-class.md)