---
title: "專案建置警告 PRJ0029 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "PRJ0029"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0029"
ms.assetid: f02c09c6-09f3-4d44-8cd4-9a25336be1ea
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 專案建置警告 PRJ0029
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法為專案層級的自訂建置步驟設定 'Outputs' 屬性，將略過自訂建置步驟。  
  
 未執行自訂建置步驟，因為未指定輸出。  
  
 若要解決這個錯誤，請執行下列任一種方法：  
  
-   將自訂建置步驟排除於組建之外。  
  
-   加入輸出。  
  
-   刪除自訂建置步驟之命令的內容。