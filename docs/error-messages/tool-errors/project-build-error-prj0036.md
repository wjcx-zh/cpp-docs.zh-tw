---
title: "專案建置錯誤 PRJ0036 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "PRJ0036"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0036"
ms.assetid: ee215cd1-2d66-474d-9a63-b9096f1c4923
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 專案建置錯誤 PRJ0036
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Web 部署工具的 'Additional Files' 屬性包含無效的項目。  
  
 Web 部署屬性頁的 Additional Files 屬性包含一個錯誤，此錯誤可能是由於巨集評估問題所造成。  此錯誤也可能表示檔案路徑的格式錯誤，其檔案路徑中包含不正確的字元或字元組合。  
  
 若要解決此問題，請修正巨集或修正路徑規格。  評估的路徑是專案目錄的絕對路徑。  
  
 此錯誤也可能表示參考的其中一個檔案不存在。