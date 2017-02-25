---
title: "專案建置警告 PRJ0042 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "PRJ0042"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0042"
ms.assetid: 682c9999-6f85-409f-b102-00c93243f74f
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# 專案建置警告 PRJ0042
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**無法為檔案 '**   
 ***file* ' 設定自訂建置步驟的 '輸出' 屬性。將略過自訂建置步驟。**  
  
 未執行自訂建置步驟，因為未指定輸出。  
  
 若要解決這個錯誤，請執行下列任一種方法：  
  
-   將自訂建置步驟排除於組建之外。  
  
-   加入輸出。  
  
-   刪除自訂建置步驟之命令的內容。