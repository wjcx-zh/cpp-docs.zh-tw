---
title: "應用程式資訊和管理 | Microsoft Docs"
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
  - "vc.mfc.macros"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "應用程式 [MFC], 管理"
ms.assetid: b72f4154-24db-4e75-bca3-6873e2459c15
caps.latest.revision: 17
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 應用程式資訊和管理
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

當您撰寫應用程式時，會建立唯一 [CWinApp](../../mfc/reference/cwinapp-class.md)衍生物件。  通常，您可以從 `CWinApp`傳出取得有關這個物件衍生物件的資訊。  
  
 MFC 程式庫提供下列全域函式可協助您完成下列工作:  
  
### 應用程式資訊和管理功能  
  
|||  
|-|-|  
|[AfxBeginThread](../Topic/AfxBeginThread.md)|建立新的執行緒。|  
|[AfxEndThread](../Topic/AfxEndThread.md)|結束目前的執行緒。|  
|[AfxFreeLibrary](../Topic/AfxFreeLibrary.md)|要載入的動態連結程式庫 \(DLL\) \(DLL\) 模組的參考次數;在參考計數達到零時，模組未對應。|  
|[AfxGetApp](../Topic/AfxGetApp.md)|將指標傳回至應用程式的單一 `CWinApp` 物件。|  
|[AfxGetAppName](../Topic/AfxGetAppName.md)|傳回包含應用程式名稱的字串。|  
|[AfxGetInstanceHandle](../Topic/AfxGetInstanceHandle.md)|傳回表示應用程式的這個執行個體的 `HINSTANCE` 。|  
|[AfxGetMainWnd](../Topic/AfxGetMainWnd.md)|將指標傳回至非 OLE 應用程式目前的主要視窗或伺服器應用程式的就地框架視窗。|  
|[AfxGetPerUserRegistration](../Topic/AfxGetPerUserRegistration.md)|使用這個函式會判斷應用程式是否已設定為 **HKEY\_CURRENT\_USER** \(**HKCU**\) 節點的登錄存取方向。|  
|[AfxGetResourceHandle](../Topic/AfxGetResourceHandle.md)|將 `HINSTANCE` 傳回至應用程式的預設資源的來源。  使用此直接存取應用程式的資源。|  
|[AfxGetThread](../Topic/AfxGetThread.md)|擷取指標目前的 [CWinThread](../../mfc/reference/cwinthread-class.md) 物件。|  
|[AfxInitRichEdit](../Topic/AfxInitRichEdit.md)|初始化應用程式的版本 1.0 Rich Edit 控制項。|  
|[AfxInitRichEdit2](../Topic/AfxInitRichEdit2.md)|使用 2.0 版和應用程式的最新 Rich Edit 控制項。|  
|[AfxLoadLibrary](../Topic/AfxLoadLibrary.md)|會將 DLL 模組並傳回可用來取得 DLL 函式的位址的控制代碼。|  
|[AfxRegisterClass](../Topic/AfxRegisterClass.md)|註冊在使用 MFC DLL 的視窗類別。|  
|[AfxRegisterWndClass](../Topic/AfxRegisterWndClass.md)|註冊 Windows 視窗類別補充 MFC 自動註冊的項目。|  
|[AfxSetPerUserRegistration](../Topic/AfxSetPerUserRegistration.md)|設定應用程式是否已設定為 **HKEY\_CURRENT\_USER** \(**HKCU**\) 節點的登錄存取方向。|  
|[AfxSetResourceHandle](../Topic/AfxSetResourceHandle.md)|設定應用程式預設資源載入的 `HINSTANCE` 控制代碼。|  
|[AfxSocketInit](../Topic/AfxSocketInit.md)|會在 `CWinApp::InitInstance` 覆寫初始化 Windows Sockets。|  
|[AfxWinInit](../Topic/AfxWinInit.md)|由 MFC 所提供的 `WinMain` 函式，做為以 GUI 應用程式的 [CWinApp](../../mfc/reference/cwinapp-class.md) 初始化一部分，初始化 MFC。  必須直接使用 MFC 的主控台應用程式呼叫。|  
  
## 請參閱  
 [巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)   
 [CWinApp Class](../../mfc/reference/cwinapp-class.md)