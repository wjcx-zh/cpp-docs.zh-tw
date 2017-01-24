---
title: "建立簡單唯讀提供者 | Microsoft Docs"
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
  - "OLE DB 提供者樣板, 建立提供者"
  - "OLE DB 提供者, 建立"
ms.assetid: ade8ccdd-9ea4-4e46-a964-18460c2a2401
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 建立簡單唯讀提供者
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在您使用 ATL 專案精靈和 ATL OLE DB 提供者精靈建立 OLE DB 提供者之後，可再加入想要支援的其他功能。  藉由檢查想要傳送消費者的資料種類，以及在何種狀況下傳送，來開始設計您的提供者。  決定是否需要支援命令、交易和其他的選擇性物件是特別重要的。  一個良好的前端設計可加速實作 \(Implementation\) 和測試。  
  
 本範例分為兩個部分：  
  
-   第一部分說明如何[建立簡單唯讀提供者](../../data/oledb/implementing-the-simple-read-only-provider.md)以讀取字串配對。  
  
-   第二部分顯示說明加入 `IRowsetLocate` 介面來[增強簡單唯讀提供者](../../data/oledb/enhancing-the-simple-read-only-provider.md)。  
  
## 請參閱  
 [建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)