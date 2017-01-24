---
title: "安裝 MFC 資料庫支援 | Microsoft Docs"
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
  - "DAO [C++], 安裝元件"
  - "資料庫 [C++], 安裝資料庫支援"
  - "資料庫 [C++], MFC"
  - "安裝 DAO"
  - "安裝 ODBC"
  - "ODBC 元件 [C++], 安裝"
  - "ODBC 驅動程式 [C++], 安裝"
ms.assetid: a6c2fc84-9e0e-4f39-a464-0bcbc415b946
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 安裝 MFC 資料庫支援
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

##  <a name="_core_odbc_drivers_installed"></a> 安裝的 ODBC 驅動程式  
 安裝程式會安裝下列 ODBC 驅動程式：  
  
-   Microsoft Access 驅動程式  
  
-   Microsoft dBASE 驅動程式  
  
-   Microsoft Excel 驅動程式  
  
-   Microsoft FoxPro VFP 驅動程式  
  
-   Microsoft Visual FoxPro 驅動程式  
  
-   Microsoft ODBC for Oracle 驅動程式  
  
-   Microsoft Paradox 驅動程式  
  
-   Microsoft Text 驅動程式  
  
-   Microsoft SQL Server 驅動程式  
  
 如需取得其他驅動程式以及本版 Visual C\+\+ 所包含的 ODBC 驅動程式清單的詳細資訊，請參閱 [ODBC 驅動程式清單](../data/odbc/odbc-driver-list.md)。  
  
##  <a name="_core_odbc_sdk_components_installed"></a> 安裝的 ODBC SDK 元件  
 Visual C\+\+ 包含許多重要的 ODBC 元件，包括所需的標頭檔 \(Header File\)、程式庫、動態連結程式庫 \(DLL\) 和工具。  還包括用來設定 ODBC 資料來源的 ODBC 管理員控制台應用程式和 ODBC 驅動程式管理員。  也包括許多普遍使用的資料庫管理系統 \(DBMS\) 的 ODBC 驅動程式，如[安裝的 ODBC 驅動程式](#_core_odbc_drivers_installed)中所列。  
  
 ODBC SDK 提供撰寫和測試 ODBC 驅動程式的額外資訊和工具。  請注意，在 Visual C\+\+ .NET 中，ODBC SDK 不再包含於 Visual C\+\+ .NET 安裝媒體中，而是屬於以 Visual Studio .NET 必要條件所安裝的 [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] 一部分。  
  
##  <a name="_core_dao_sdk_components_installed"></a> 安裝的 SDK 元件  
  
> [!NOTE]
>  Microsoft 建議於新專案使用 OLE DB 或 ODBC。  DAO 應僅用於維護現有的應用程式。  
  
 在預設狀況下會安裝下列 DAO SDK 元件：  
  
-   Microsoft Jet \(4.0 SP3\)  
  
-   Microsoft Jet \(3.x MDB\)  
  
-   Microsoft Jet \(1.x、2.x\)  
  
-   所有列於以下主題中的資料庫格式：[我可使用 DAO 和 ODBC 存取什麼資料庫？](../data/what-data-sources-can-i-access-with-dao-and-odbc-q.md)  
  
 在 Visual C\+\+ .NET 中，DAO SDK 將和 Visual Studio .NET 必要條件一起安裝。  請執行 \\Jet\\Jetsetup.exe。  
  
> [!NOTE]
>  Microsoft 建議使用 Jet 4.0 Service Pack 3 \(2927.04 版\) 或更新版本。  Jet 4.0 Service Pack 3 隨附於 Windows 2000 和 Windows Me 中。  使用這個版本的 Jet，可以減少應用程式所必須測試的 Jet 版本數目。  Windows XP 可能推出另一版的 Jet。  請參閱[轉散發控制項](../data/ado-rdo/redistributing-controls.md)中的「有關轉散發 DAO 元件的說明」。  
  
 如果您想要安裝其他的 DAO SDK 元件，例如，DAO SDK C\+\+ 類別、範例檔或 DAO 說明檔的 Windows 說明版本，請從 Visual C\+\+ 6.0 光碟上安裝 DAO SDK。  
  
 如需 OLE DB 更新和最新消息，請參閱通用資料存取網站 [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=121548](http://go.microsoft.com/fwlink/?LinkId=121548)。  
  
## 請參閱  
 [Data Access Programming \(MFC\/ATL\)](../data/data-access-programming-mfc-atl.md)