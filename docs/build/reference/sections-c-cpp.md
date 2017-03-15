---
title: "SECTIONS (C/C++) | Microsoft Docs"
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
  - "SECTIONS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SECTIONS .def 檔案陳述式"
ms.assetid: 7b974366-9ef5-4e57-bbcc-73a1df6f8857
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# SECTIONS (C/C++)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

加入包含一或多個 `definitions` 的區段，這些定義是在專案輸出檔案中區段的存取規範。  
  
```  
SECTIONS  
definitions  
```  
  
## 備註  
 每一個定義都必須寫在不同的程式行中。  `SECTIONS` 關鍵字可以和第一個定義位於同一行或前一行。  .def 檔可以包含一個或多個 `SECTIONS` 陳述式。  
  
 這個 `SECTIONS` 陳述式設定映像檔中一個或多個區段的屬性，並可用來覆寫每一種區段類型的預設屬性。  
  
 `definitions` 的格式是：  
  
 `.section_name specifier`  
  
 其中 `.section_name` 是程式映像中的區段名稱，`specifier` 則是下列其中一個或多個存取修飾詞：  
  
|修飾詞|說明|  
|---------|--------|  
|`EXECUTE`|這個區段可以執行|  
|`READ`|允許資料讀取作業|  
|`SHARED`|與載入影像的所有處理序共用區段|  
|`WRITE`|允許資料寫入作業|  
  
 請以空格分隔規範名稱。  例如：  
  
```  
SECTIONS  
.rdata READ WRITE  
```  
  
 `SECTIONS` 會標記區段 `definitions` 清單的開頭。  每個`definition` 必須單獨一行。  `SECTIONS` 關鍵字可以位在第一個 `definition` 的同一行或上一行。  .def 檔可以包含一個或多個 `SECTIONS` 陳述式。  `SEGMENTS` 關鍵字是當做 `SECTIONS` 的同義字來支援。  
  
 舊版的 Visual C\+\+ 支援：  
  
```  
section [CLASS 'classname'] specifier  
```  
  
 `CLASS` 關鍵字是為了相容性而支援的，但已捨棄不用。  
  
 指定區段屬性的另一種方式是使用 [\/SECTION](../../build/reference/section-specify-section-attributes.md) 選項。  
  
## 請參閱  
 [模組定義陳述式的規則](../../build/reference/rules-for-module-definition-statements.md)