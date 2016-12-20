---
title: "MFC 模組狀態的啟用內容支援 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "啟用內容 [C++]"
  - "啟用內容 [C++], MFC 支援"
ms.assetid: 1e49eea9-3620-46dd-bc5f-d664749567c7
caps.latest.revision: 14
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC 模組狀態的啟用內容支援
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 建立啟動內容使用使用者模組所提供的資訊清單資源。  如需啟動內容的詳細資訊，請參閱下列主題:  
  
-   [Activation Contexts](http://msdn.microsoft.com/library/aa374153)  
  
-   [Application Manifests](http://msdn.microsoft.com/library/aa374191)  
  
-   [Assembly Manifests](http://msdn.microsoft.com/library/aa374219)  
  
## 備註  
 當讀取這些 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)] 主題時，請注意 MFC 啟動內容機制類似 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)] 啟動內容，除了 MFC 不使用 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)] 啟動內容應用程式開發介面。  
  
 啟動內容在 MFC 應用程式、使用者 DLL 和擴充 DLL 以下列方式運作:  
  
-   MFC 應用程式為它們的資訊清單資源使用資源 ID 1。  在這種情況下， MFC 不建立它的啟動內容，而是使用預設的應用程式內容。  
  
-   MFC 使用者 DLL 使用它們的資訊清單資源的資源 ID 2。  在這裡， MFC 會為每個使用者 DLL 的啟動內容，因此，其他使用者 DLL 可以使用相同的程式庫 \(例如，通用控制項程式庫\) 的不同版本。  
  
-   MFC 擴充 DLL 相依於其裝載應用程式或使用者 DLL 建立它們的啟動內容。  
  
 雖然啟動內容狀態中修改使用處理序會描述在 [Using the Activation Context API](http://msdn.microsoft.com/library/aa376620)下，使用 MFC 啟動內容機制很有用，在開發不容易以 DLL 的外掛程式結構 \(或無法\) 手動轉換成啟動狀態在個別的呼叫前後外部插入。  
  
 啟動內容在 [AfxWinInit](../Topic/AfxWinInit.md)建立。  會在 `AFX_MODULE_STATE` 解構函式被終結。  啟動內容控制代碼在 `AFX_MODULE_STATE`被保留。\(`AFX_MODULE_STATE`將在[AfxGetStaticModuleState](../Topic/AfxGetStaticModuleState.md)中加以說明。\)  
  
 [AFX\_MANAGE\_STATE](../Topic/AFX_MANAGE_STATE.md) 巨集啟動和停用啟動內容。  `AFX_MANAGE_STATE` 為 MFC 靜態程式庫，以及 MFC DLL 啟用，允許 MFC 程式碼在使用者 DLL 選取適當的啟動內容執行。  
  
## 請參閱  
 [Activation Contexts](http://msdn.microsoft.com/library/aa374153)   
 [Application Manifests](http://msdn.microsoft.com/library/aa374191)   
 [Assembly Manifests](http://msdn.microsoft.com/library/aa374219)   
 [AfxWinInit](../Topic/AfxWinInit.md)   
 [AfxGetStaticModuleState](../Topic/AfxGetStaticModuleState.md)   
 [AFX\_MANAGE\_STATE](../Topic/AFX_MANAGE_STATE.md)