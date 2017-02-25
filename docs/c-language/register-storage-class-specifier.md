---
title: "register 儲存類別規範 | Microsoft Docs"
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
  - "register 儲存類別"
  - "register 變數"
ms.assetid: 7577bf48-88ec-4191-873c-ef4217a4034e
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# register 儲存類別規範
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 Microsoft C\/C\+\+ 編譯器不接受使用者要求的暫存器變數。  不過，為了提供可攜性，編譯器接受其他所有與 **register** 關鍵字相關的語意。  例如，您不能對暫存器物件套用一元傳址運算子 \(**&**\)，也無法在陣列上使用 **register** 關鍵字。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [內部層級宣告的儲存類別規範](../c-language/storage-class-specifiers-for-internal-level-declarations.md)