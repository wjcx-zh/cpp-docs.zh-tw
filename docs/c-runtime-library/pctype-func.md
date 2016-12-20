---
title: "__pctype_func | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "__pctype_func"
apilocation: 
  - "msvcrt.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr120.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr80.dll"
apitype: "DLLExport"
f1_keywords: 
  - "__pctype_func"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__pctype_func"
ms.assetid: d52b8add-d07d-4516-a22f-e836cde0c57f
caps.latest.revision: 2
caps.handback.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __pctype_func
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

擷取字元分類資訊的指標。  
  
## 語法  
  
```cpp  
const unsigned short *__pctype_func(  
   )  
```  
  
## 傳回值  
 字元分類資訊的指標。  
  
## 備註  
 字元類別表中的資訊僅供內部使用，並為各種使用型別為 `char` 的分類字元的函式所使用。  如需詳細資訊，請參閱[\_pctype、\_pwctype、\_wctype、\_mbctype、\_mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md) 的`Remarks`一節。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|\_\_pctype\_func|ctype.h|  
  
## 請參閱  
 [\_pctype、\_pwctype、\_wctype、\_mbctype、\_mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md)