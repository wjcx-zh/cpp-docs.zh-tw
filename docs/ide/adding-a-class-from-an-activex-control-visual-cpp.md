---
title: "自 ActiveX 控制項加入類別 (Visual C++) | Microsoft Docs"
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
  - "ActiveX 控制項 [C++], 加入類別"
  - "類別 [C++], 建立"
ms.assetid: 729fcb37-54b8-44d5-9b4e-50bb16e0eea4
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 自 ActiveX 控制項加入類別 (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用這個精靈從可用 ActiveX 控制項的介面建立 MFC 類別 \(Class\)。  您可以將 MFC 類別加入至 [MFC 應用程式](../mfc/reference/creating-an-mfc-application.md)、[MFC DLL](../mfc/reference/creating-an-mfc-dll-project.md) 或 [MFC ActiveX 控制項](../mfc/reference/creating-an-mfc-activex-control.md)中。  
  
> [!NOTE]
>  您不需要啟用 Automation 建立 MFC 專案，就能從 ActiveX 控制項加入類別。  
  
 ActiveX 控制項是以元件物件模型 \(Component Object Model，COM\) 為基礎的重複使用軟體元件，可支援各種不同的 OLE 功能，也能夠自訂來符合許多軟體需求。  ActiveX 控制項是設計來用於一般 ActiveX 控制項容器，以及網際網路上的全球資訊網 \(World Wide Web\) 網頁中。  
  
### 若要從 ActiveX 控制項加入 MFC 類別  
  
1.  在**方案總管**或[類別檢視](http://msdn.microsoft.com/zh-tw/8d7430a9-3e33-454c-a9e1-a85e3d2db925)中，以滑鼠右鍵按一下您要加入 ActiveX 控制項類別的專案名稱。  
  
2.  在捷徑功能表中，按一下 \[加入\] 後再按一下 \[加入類別\]。  
  
3.  在[加入類別](../ide/add-class-dialog-box.md)對話方塊的 \[樣板\] 窗格中，按一下 \[來自 ActiveX 控制項的 MFC 類別\]，然後按一下 \[開啟\]，以顯示[加入來自 ActiveX 控制項的類別精靈](../ide/add-class-from-activex-control-wizard.md)。  
  
 在精靈中，您可加入多個 ActiveX 控制項裡的介面。  同樣地，您可於單一精靈工作階段 \(Session\) 中自多個 ActiveX 控制項建立類別。  
  
 您可以從已登錄在系統中的 ActiveX 控制項加入類別，或者從位於型別程式庫檔案 \(Type Library File，例如 .tlb、.olb、.dll、.ocx 或 .exe\) 中且尚未先在系統登錄的 ActiveX 控制項加入類別。  如需登錄 ActiveX 控制項的詳細資訊，請參閱[登錄 OLE 控制項](../mfc/reference/registering-ole-controls.md)。  
  
 精靈會為每一個從選取之 ActiveX 控制項加入的介面，建立一個衍生自 [CWnd](../mfc/reference/cwnd-class.md) 或 [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md) 的 MFC 類別。  
  
## 請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   
 [Introduction to COM and ATL](../atl/introduction-to-com-and-atl.md)