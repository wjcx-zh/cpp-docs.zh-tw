---
title: "codecvt_utf16 | Microsoft Docs"
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
  - "codecvt/std::codecvt_utf16"
  - "std::codecvt_utf16"
  - "std.codecvt_utf16"
  - "codecvt_utf16"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "codecvt_utf16 類別"
ms.assetid: a9897f98-f84d-4db6-90ad-858b2727570c
caps.latest.revision: 21
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# codecvt_utf16
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

代表 [地區設定](../standard-library/locale-class.md) ucs\-2 為 ucs\-4 編碼的寬字元和編碼為 UTF\-8 16LE 或 UTF 16BE 位元組資料流之間進行轉換的 facet。  
  
## 語法  
  
```  
template<  
    class Elem,  
    unsigned long Maxcode = 0x10ffff,  
    codecvt_mode Mode = (codecvt_mode)0  
>  
class codecvt_utf16 : public std::codecvt<Elem, char, StateType>  
```  
  
#### 參數  
  
|參數|描述|  
|--------|--------|  
|`Elem`|寬字元項目類型。|  
|`Maxcode`|地區設定 facet 的字元數目上限。|  
|`Mode`|地區設定 facet 的組態資訊。|  
  
## 備註  
 此範本類別轉換寬字元的 ucs\-2 為 ucs\-4 編碼和位元組資料流編碼為 UTF\-8 16LE，如果 `Mode & little_endian`, ，或 UTF 16BE 其他方式。  
  
 位元組資料流應該寫入至二進位檔案。如果寫入到文字檔案，它可能會損毀。  
  
## 需求  
 **標頭︰** \< codecvt \>  
  
 **命名空間:** std