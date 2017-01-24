---
title: "位址的儲存 | Microsoft Docs"
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
  - "位址 [C++], 的儲存"
  - "儲存 [C++], 位址"
ms.assetid: 423b2402-b847-4788-ad70-943b7c9c5c8b
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 位址的儲存
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

位址所需的儲存數量和位址的意義取決於編譯器的實作。  不同類型的指標不一定會具有相同長度。  因此，**sizeof\(char \*\)** 不一定等於 **sizeof\(int \*\)**。  
  
 **Microsoft 特定的**  
  
 對於 Microsoft C 編譯器，**sizeof\(char \*\)** 等於 **sizeof\(int \*\)**。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [指標宣告](../c-language/pointer-declarations.md)