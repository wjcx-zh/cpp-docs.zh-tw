---
title: "Naked (C) | Microsoft Docs"
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
  - "終解程式碼"
  - "naked 關鍵字 [C]"
  - "naked 關鍵字 [C], 儲存類別屬性"
  - "初構程式碼"
ms.assetid: 23b1209b-93ba-46ad-a60f-2327c1933eaf
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Naked (C)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 naked 儲存類別屬性是 Microsoft 專有的 C 語言擴充功能。  編譯器會針對以 naked 儲存類別屬性宣告的函式，產生不具初構和終解程式碼的程式碼。  當您需要使用內嵌組合語言程式碼撰寫自己的初構\/終解程式碼序列時，naked 函式會很有用。  naked 函式在撰寫虛擬裝置驅動程式方面也很實用。  
  
 如需使用 naked 屬性的專屬資訊，請參閱 [Naked 函式](../c-language/naked-functions.md)。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [C 擴充的儲存類別屬性](../c-language/c-extended-storage-class-attributes.md)