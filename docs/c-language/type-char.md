---
title: "類型 char | Microsoft Docs"
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
  - "char 關鍵字 [C]"
  - "類型 char"
  - "unsigned char 關鍵字 [C]"
ms.assetid: a5da0866-e780-4793-be87-15a8426e7ea0
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 類型 char
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`char` 類型可用來儲存可顯示字元集之成員的整數值。  該整數值是對應所指定字元的 ASCII 碼。  
  
 **Microsoft 特定的**  
  
 `unsigned char` 類型的字元值範圍是十六進位的 0 到 0xFF。  **signed char** 的範圍是 0x80 到 0x7F。  這些範圍會分別轉譯為十進位的 0 到 255 及十進位的 – 128 到 \+127。  \/J 編譯器選項將預設值從 **signed** 變更為 `unsigned`。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [基本類型的儲存空間](../c-language/storage-of-basic-types.md)