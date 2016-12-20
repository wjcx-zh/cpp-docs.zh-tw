---
title: "DAO 資料庫引擎初始化及終止 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros.data"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DAO (資料存取物件), 初始化"
  - "DAO (資料存取物件), 終止"
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
caps.latest.revision: 13
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# DAO 資料庫引擎初始化及終止
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

當使用 MFC DAO 物件時，必須在應用程式或 DLL 退出前先初始化然後終止 DAO 資料庫引擎。  兩個函式， `AfxDaoInit` 和 `AfxDaoTerm` 執行這些工作。  
  
### DAO 資料庫引擎初始化及終止  
  
|||  
|-|-|  
|[AfxDaoInit](../Topic/AfxDaoInit.md)|初始化 DAO 資料庫引擎。|  
|[AfxDaoTerm](../Topic/AfxDaoTerm.md)|結束 DAO 資料庫引擎。|  
  
## 請參閱  
 [巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)