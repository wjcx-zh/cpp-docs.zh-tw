---
title: "Adding an ATL Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 專案, 加入對話方塊資源"
  - "對話方塊, ATL"
  - "MFC 對話方塊, ATL 對話方塊"
ms.assetid: 152a378f-7b24-4f66-aeba-c740973f03a6
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Adding an ATL Dialog Box
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

若要將 ATL 對話方塊加入至您的專案，您的專案必須是 ATL 專案或包含 ATL 支援的 MFC 專案。  您可以使用 [ATL 專案精靈](../../atl/reference/atl-project-wizard.md)來建立 ATL 應用程式，或[將 ATL 支援加入至 MFC 專案](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)來為 MFC 應用程式實作 ATL 支援。  
  
 依照預設，ATL 對話方塊精靈會實作衍生自 [CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md) 的對話方塊。  這個類別 \(Class\) 包含裝載 \(Host\) ActiveX 和 Windows 控制項 \(Control\) 的支援。  如果您不要 ActiveX 控制項支援的負荷，則在精靈一產生的程式碼時，就利用 [CSimpleDialog](../../atl/reference/csimpledialog-class.md) 或 [CDialogImpl](../../atl/reference/cdialogimpl-class.md) 當做基底類別 \(Base Class\)，來取代 `CAxDialogImpl` 的所有執行個體 \(Instance\)。  
  
> [!NOTE]
>  `CSimpleDialog` 僅建立只支援 Windows 通用控制項的強制回應對話方塊。  `CDialogImpl` 則可建立強制回應或非強制回應對話方塊。  
  
### 若要將 ATL 對話方塊資源加入至您的專案  
  
1.  使用 [ATL 專案精靈](../../atl/reference/atl-project-wizard.md)建立 ATL 專案。  
  
2.  從[類別檢視](http://msdn.microsoft.com/zh-tw/8d7430a9-3e33-454c-a9e1-a85e3d2db925)中，以滑鼠右鍵按一下專案名稱，然後從捷徑功能表按一下 \[加入\]。  按一下 \[加入類別\]。  
  
3.  在[加入類別](../../ide/add-class-dialog-box.md)對話方塊的 \[範本\] 窗格中按一下 \[ATL 對話方塊\]。  按一下 \[開啟\] 以顯示 [ATL 對話方塊精靈](../../atl/reference/atl-dialog-wizard.md)。  
  
 如需詳細資訊，請參閱[實作對話方塊](../../atl/implementing-a-dialog-box.md)。  
  
## 請參閱  
 [加入類別](../../ide/adding-a-class-visual-cpp.md)   
 [視窗類別](../../atl/atl-window-classes.md)   
 [Message Maps](../../atl/message-maps-atl.md)