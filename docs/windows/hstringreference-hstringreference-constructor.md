---
title: "HStringReference::HStringReference 建構函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HStringReference::HStringReference"
dev_langs: 
  - "C++"
ms.assetid: 29f5fe11-3928-4f60-9861-f0894247bfcb
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HStringReference::HStringReference 建構函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

初始化 HStringReference 類別的新執行個體。  
  
## 語法  
  
```cpp  
  
    template<unsigned int sizeDest>  
    HStringReference(wchar_t const (&str)[ sizeDest]) throw();  
  
    template<unsigned int sizeDest>  
    HStringReference(wchar_t const (&str)[ sizeDest],   
unsigned int len)  
       throw();  
  
    HStringReference(HStringReference&& other) throw();  
  
```  
  
#### 參數  
 `sizeDest`  
 指定目的 HStringReference 緩衝區大小的樣板參數。  
  
 `str`  
 寬字元字串的參考。  
  
 `len`  
 在這項作業使用的 `str` 參數緩衝區的最大長度。  如果 `len` 未指定參數，則會使用整個 `str` 參數。  如果 `len` 比 `sizeDest`大於， `len` 設為 `sizeDest`\-1。  
  
 `other`  
 另一 HStringReference 物件。  
  
## 備註  
 第一個建構函式會初始化一個與參數 `str`相同大小的新 HStringReference 物件。  
  
 第二個建構函式會初始化一個由參數 `len`所指定大小的新 HStringReference 物件。  
  
 第三個建構函式會用 `other`參數的值初始化新的 HStringReference 物件，然後終結 `other` 參數。  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間：**Microsoft::WRL::Wrappers  
  
## 請參閱  
 [HStringReference 類別](../windows/hstringreference-class.md)