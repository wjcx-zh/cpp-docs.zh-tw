---
title: "C 大小整數類型 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "大小整數類型"
ms.assetid: 0d6199b4-d0ab-4e8c-a769-785f5afb92eb
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C 大小整數類型
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 Microsoft C 的功能支援可調整大小的整數類型。  您可以使用 \_\_int*n* 類型規範來宣告 8、16、32 或 64 位元的整數變數，其中 *n* 為整數變數的大小 \(以位元為單位\)。  *n* 的值可以是 8、16、32 或 64。  下列範例宣告了四種可調整大小整數類型的變數：  
  
```  
__int8 nSmall;      // Declares 8-bit integer  
__int16 nMedium;    // Declares 16-bit integer  
__int32 nLarge;     // Declares 32-bit integer  
__int64 nHuge;      // Declares 64-bit integer  
```  
  
 前三類可調整大小的整數與具有相同大小的 ANSI 類型同義，且當撰寫可移植程式碼的行為模式在多個平台上完全相同時，這也會很有用。  請注意，\_\_int8 資料類型與 char 類型同義，\_\_int16 與 short 類型同義，而 \_\_int32 和 int 類型同義。  \_\_int64 類型沒有對等的 ANSI 對應項目。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [基本類型的儲存空間](../c-language/storage-of-basic-types.md)