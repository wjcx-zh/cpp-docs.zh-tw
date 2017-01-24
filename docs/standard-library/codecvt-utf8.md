---
title: "codecvt_utf8 | Microsoft Docs"
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
  - "std.codecvt_utf8"
  - "std::codecvt_utf8"
  - "codecvt_utf8"
  - "codecvt/std::codecvt_utf8"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "codecvt_utf8 類別"
ms.assetid: 2a87478f-e2d4-4b8d-ad9c-00add01d1bb0
caps.latest.revision: 20
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# codecvt_utf8
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示 [地區設定](../standard-library/locale-class.md) Facet 轉譯為\) 輸入的寬字元或 UCS\-4 和之間以 UTF\-8 編碼的位元組資料流。  
  
## 語法  
  
```  
template<  
    class Elem,  
    unsigned long Maxcode = 0x10ffff,  
    codecvt_mode Mode = (codecvt_mode)0  
>  
class codecvt_utf8 : public std::codecvt<Elem, char, StateType>  
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