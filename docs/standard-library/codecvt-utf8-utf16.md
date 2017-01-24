---
title: "codecvt_utf8_utf16 | Microsoft Docs"
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
  - "codecvt_utf8_utf16"
  - "codecvt/std::cvt_utf8_utf16"
  - "std::codecvt_utf8_utf16"
  - "std.codecvt_utf8_utf16"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "codecvt_utf8_utf16 類別"
ms.assetid: 4c12c881-5dba-4e39-b338-0b9caff5af29
caps.latest.revision: 21
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# codecvt_utf8_utf16
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示 [地區設定](../standard-library/locale-class.md) 轉換為 UTF\-16 編碼的寬字元和以 UTF\-8 編碼的位元組資料流之間的 Facet。  
  
## 語法  
  
```  
template<  
    class Elem,  
    unsigned long Maxcode = 0x10ffff,  
    codecvt_mode Mode = (codecvt_mode)0  
>  
class codecvt_utf8_utf16 : public _STD codecvt<Elem, char, StateType>  
```  
  
#### 參數  
  
|參數|說明|  
|--------|--------|  
|`Elem`|寬字元項目型別。|  
|`Maxcode`|最大字元數地區設定的 Facet。|  
|`Mode`|地區設定之 facet 組態資訊。|  
  
## 備註  
 位元組資料流可寫入二進位檔案或文字檔。  
  
## 需求  
 **標題:** \<codecvt\>  
  
 **命名空間:** std