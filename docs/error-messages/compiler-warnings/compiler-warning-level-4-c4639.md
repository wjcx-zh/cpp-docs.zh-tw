---
title: "編譯器警告 (層級 4) C4639 | Microsoft Docs"
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
  - "C4639"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4639"
ms.assetid: f94f7392-cdbb-4bf4-8a00-20dc90d3efe9
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4639
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

MSXML 錯誤，將不會處理 XML 文件註解。原因  
  
 這項警告可能會因為任何理由而造成。  
  
 若要解除這項警告：  
  
-   請重新編譯。  
  
-   透過重新安裝 Common Language Runtime，重新安裝 MSXML。  
  
-   編輯或移除造成警告的文件註解，並重新編譯。  
  
 發出 C4639 時，所有進一步的 XML 註解處理都會停用，而且不產生 .xdc 檔。