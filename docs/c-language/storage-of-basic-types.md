---
title: "基本類型的儲存空間 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "算術運算 [C++], 類型"
  - "資料類型 [C], 規範"
  - "資料類型 [C], 儲存體"
  - "double 資料類型, 儲存體"
  - "浮點數, 儲存體"
  - "int 資料類型"
  - "整數類型"
  - "整數類型, 儲存體"
  - "long double 關鍵字 [C], 儲存體"
  - "long 關鍵字 [C]"
  - "short 資料類型"
  - "signed 類型 [C++], 儲存體"
  - "規範 [C++], 類型"
  - "儲存 [C++], 類型"
  - "儲存類型 [C++]"
  - "類型規範 [C++], 大小"
  - "類型 [C], 算術"
  - "unsigned 類型 [C++], 儲存體"
ms.assetid: bd1f33c1-c6b9-4558-8a72-afb21aef3318
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 基本類型的儲存空間
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下表摘要說明與每個基本類型相關聯的儲存區。  
  
### 基本類型的大小  
  
|類型|儲存區|  
|--------|---------|  
|`char`、`unsigned char`、**signed char**|1 個位元組|  
|**short**、**unsigned short**|2 個位元組|  
|`int`, `unsigned int`|4 個位元組|  
|**long**、`unsigned long`|4 個位元組|  
|**float**|4 個位元組|  
|**double**|8 個位元組|  
|`long double`|8 個位元組|  
  
 C 資料類型屬於一般分類。  「整數類資料類型」包括 `char`、`int`、**short**、**long**、**signed**、`unsigned` 和 `enum`。  「浮點類型」包括 **float**、**double** 和 `long double`。  「算術類型」包括所有浮點和整數類資料類型。  
  
## 請參閱  
 [宣告和類型](../c-language/declarations-and-types.md)