---
title: "offsetof 巨集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "offsetof"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "offsetof 巨集"
  - "結構成員, 位移"
ms.assetid: f3b4eb16-a882-4d38-afc9-eebd976a7352
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# offsetof 巨集
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從其父結構開頭擷取成員的位移。  
  
## 語法  
  
```  
  
        size_t offsetof(  
   structName,  
   memberName   
);  
```  
  
#### 參數  
 *structName*  
 父資料結構的名稱。  
  
 `memberName`  
 要判斷其位移之父資料結構中成員的名稱。  
  
## 傳回值  
 `offsetof` 會傳回所指定成員從其父資料結構開頭的位移 \(位元組\)。  位元欄位並未定義它。  
  
## 備註  
 `offsetof` 巨集會將 `memberName` 從 *structName* 所指定結構開頭的位移 \(位元組\) 傳回類型為 `size_t` 的值。  您可以指定類型與 `struct` 關鍵字。  
  
> [!NOTE]
>  `offsetof` 不是函式，而且無法使用 C 原型進行描述。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`offsetof`|\<stddef.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## 請參閱  
 [記憶體配置](../../c-runtime-library/memory-allocation.md)