---
title: "BSCMAKE 錯誤 BK1517 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "BK1517"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BK1517"
ms.assetid: 24391f42-0a3e-40a9-9991-c8b9a6a7b1c7
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# BSCMAKE 錯誤 BK1517
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'sbrfile' 的原始程式檔是以 \/Yc 和 \/Yu 編譯  
  
 此 .sbr 檔案參考其本身。  可能是因為以 \/Yc 編譯後又再以 \/Yu 重新編譯。  重新設定原始程式檔的編譯器選項為 \/Yc，然後選取 \[重建\] 以產生新的 .sbr 檔案。  請不要再以 \/Yu 重新編譯原始程式檔。