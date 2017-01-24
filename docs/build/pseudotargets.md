---
title: "虛擬目標 | Microsoft Docs"
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
helpviewer_keywords: 
  - "Makefile, 虛擬目標"
  - "NMAKE 程式, 虛擬目標"
  - "NMAKE 程式, 目標"
  - "虛擬目標與 NMAKE"
  - "時間戳記, makefile 虛擬目標"
ms.assetid: c8c479dc-0129-4186-8366-bc6251f2b494
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 虛擬目標
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

虛擬目標是個標籤，用來取代在相依性行中的檔名。  會將它解譯成不存在而且過時的檔案。  NMAKE 會假設虛擬目標的時間戳記是所有相依性中最新的時間戳記。  如果沒有相依性，就會假設為目前的時間。  如果虛擬目標是用來當做目標，就會永遠執行它的命令。  用來當做相依性的虛擬目標必須在另一個相依性中顯示為目標。  不過，相依性不需要具有命令區塊。  
  
 虛擬目標名稱會依照目標的檔名語法規則。  然而，如果名稱沒有副檔名 \(也就是說不含英文句號\)，就可以超過檔案名稱的 8 字元限制，最長可為 256 個字元。  
  
## 請參閱  
 [目標](../build/targets.md)