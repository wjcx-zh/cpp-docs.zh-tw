---
title: "ATL 模組類別 | Microsoft Docs"
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
  - "ATL, 模組類別"
  - "CComModule 類別, 已變更的內容"
  - "模組類別"
ms.assetid: fd75382d-c955-46ba-a38e-37728b7fa00f
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ATL 模組類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主題討論剛在 ATL 7.0 中模組的類別。  
  
## CComModule 取代類別  
 ATL 舊版所使用的 `CComModule`。  在 ATL 7.0 中， `CComModule` 功能由數個類別取代:  
  
-   [CAtlBaseModule](../atl/reference/catlbasemodule-class.md) 包含使用 ATL 的大多數應用程式所需的資訊。  包含模組和資源執行個體的 HINSTANCE。  
  
-   [CAtlComModule](../atl/reference/catlcommodule-class.md) 包含在 ATL COM 類別所需的資訊。  
  
-   [CAtlWinModule](../atl/reference/catlwinmodule-class.md) ATL 中包含 Windowing 類別所需的資訊。  
  
-   [CAtlDebugInterfacesModule](../atl/reference/catldebuginterfacesmodule-class.md) 包含支援介面進行偵錯。  
  
-   下列[CAtlModule](../atl/reference/catlmodule-class.md)`CAtlModule`衍生類別自訂在特定應用程式類型包含所需的資訊。  這些類別的大部分成員可以覆寫:  
  
    -   [CAtlDllModuleT](../atl/reference/catldllmodulet-class.md) DLL 在應用程式中使用的。  提供標準的匯出的程式碼。  
  
    -   [CAtlExeModuleT](../atl/reference/catlexemodulet-class.md) EXE 在應用程式中使用的。  提供在 EXE 所需的程式碼。  
  
    -   [CAtlServiceModuleT](../atl/reference/catlservicemodulet-class.md) 支援建立 Windows NT 和 Windows 2000 服務。  
  
 `CComModule` 回溯相容性 \(Backward Compatibility\) 是否可用。  
  
## 發出 CComModule 功能的原因  
 `CComModule` 功能發出至下列原因的幾個新的類別:  
  
-   讓 `CComModule` 的功能更細微。  
  
     支援 COM、Windowing 介面、偵錯和應用程式特定的 \(DLL 或 EXE\) 功能現在是個別的類別。  
  
-   自動宣告這些模組中的全域執行個體。  
  
     必要的模組類別的全域執行個體連接到專案中。  
  
-   移除呼叫 Init 方法時所必要。  
  
     Merge 和詞彙方法或建構函式和解構函式模組類別的;不再需要呼叫 Merge 和詞彙。  
  
## 請參閱  
 [概念](../atl/active-template-library-atl-concepts.md)   
 [Class Overview](../atl/atl-class-overview.md)