---
title: "安裝資料庫支援 (MFC/ATL) | Microsoft Docs"
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
  - "ATL [C++], 資料庫支援"
  - "資料存取 [C++], 安裝資料庫支援"
  - "資料庫 [C++], 安裝資料庫支援"
  - "安裝資料庫支援"
ms.assetid: 3820ba96-4fb8-4405-83dd-bb3bc5998667
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 安裝資料庫支援 (MFC/ATL)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您執行 Visual C\+\+ .NET 的安裝程式時，會自動安裝下列的資料庫元件：  
  
-   所有必要的 ATL OLE DB 元件。  如需詳細資訊，請參閱[安裝 ATL 資料庫支援](../data/installing-atl-database-support.md)。  
  
-   一組具有 ODBC 驅動程式管理員和 ODBC 管理員程式的 ODBC 驅動程式。  如需詳細資訊，請參閱[安裝 MFC 資料庫支援](../data/installing-mfc-database-support.md)中的「已安裝的 ODBC 驅動程式」和「已安裝的 ODBC SDK 元件」。  
  
-   DAO 軟體開發套件 \(SDK\) 中的必要元件。  這包括未與此文件整合的說明檔。  不過，如果您使用 DAO，則需要安裝與作業系統相容的 Jet 版本。  如需詳細資訊，請參閱[安裝 MFC 資料庫支援](../data/installing-mfc-database-support.md)中的「已安裝的 ODBC SDK 元件」。  
  
 安裝程式也會安裝 Microsoft 資料存取元件 \(MDAC\) \(基礎安裝的一部分\)，這是要支援在 Visual C\+\+.NET 中進行資料存取程式設計所必要的。  
  
 Visual C\+\+ .NET 安裝 MDAC 2.7 SDK。  如需 MDAC SDK 的更新和最新消息，請參閱 Microsoft 通用資料存取網站，網址為 [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=121548](http://go.microsoft.com/fwlink/?LinkId=121548)。  
  
 如果您要轉散發資料存取應用程式，則也應有 MDAC 2.7 轉散發程式。  MDAC 2.7 SDK 設計為搭配 Visual Studio .NET 必要條件 CD\-ROM 上的 MDAC 目錄中包含的 MDAC 2.7 轉散發程式 \(Mdac\_typ.exe\) 使用。  您也可以從先前列出的 MDAC 2.7 SDK 下載連結下載 Mdac\_typ.exe。  如需轉散發元件的詳細資訊，請參閱[轉散發控制項](../data/ado-rdo/redistributing-controls.md)。  
  
## 請參閱  
 [資料存取](../Topic/Data%20Access%20in%20Visual%20C++.md)