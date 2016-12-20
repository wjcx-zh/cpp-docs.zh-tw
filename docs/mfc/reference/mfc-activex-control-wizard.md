---
title: "MFC ActiveX 控制項精靈 | Microsoft Docs"
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
  - "vc.appwiz.mfc.ctl.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控制項 [C++], MFC"
  - "MFC ActiveX 控制項精靈"
  - "MFC ActiveX 控制項 [C++], 精靈"
  - "OLE 控制項 [C++]"
  - "OLE 控制項 [C++], 建立"
ms.assetid: f19d698c-bdc3-4c74-af97-3d6ccb441b75
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控制項精靈
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ActiveX 控制項是 [Automation 伺服程式](../../mfc/automation-servers.md)的特定類型；它是可重複使用的元件。  裝載 \(Host\) ActiveX 控制項的應用程式是這個控制項的 [Automation 用戶端](../../mfc/automation-clients.md)。  如果要建立這類可重複使用的元件，則請使用這個精靈來建立您的控制項。  如需詳細資訊，請參閱 [MFC ActiveX 控制項](../../mfc/mfc-activex-controls.md)。  
  
 此外，您可使用 [MFC 應用程式精靈](../../mfc/reference/mfc-application-wizard.md)來建立 Automation 伺服程式 MFC 應用程式。  
  
 使用這個精靈建立的 ActiveX 控制項可以有使用者介面，也可以是不可見的。  您可在精靈的[控制項設定](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)頁面來表示這個選項。  計時器控制項是您希望成為不可見 ActiveX 控制項的例子。  
  
 ActiveX 控制項可具有複雜的使用者介面。  有些控制項可能就像封裝的表單：包含許多欄位的單一控制項，每個欄位都有適當的 Windows 控制項。  例如，一個實作為 MFC ActiveX 控制項的汽車零件物件可能有個像表單的使用者介面，使用者透過這個介面可讀取並編輯零件編號、零件名稱以及其他資訊。  如需詳細資訊，請參閱 [MFC ActiveX 控制項](../../mfc/mfc-activex-controls.md)。  
  
 如需為 ActiveX 物件建立容器 \(Container\)，請參閱[建立 ActiveX 控制項容器](../../mfc/reference/creating-an-mfc-activex-control-container.md)。  
  
 MFC 起始程式包含 C\+\+ 原始程式 \(.cpp\) 檔、資源 \(.rc\) 檔及專案 \(.vcxproj\) 檔。  起始檔案 \(Starter File\) 中所產生的程式碼是以 MFC 為基礎。  
  
 以下範例清單顯示 ActiveX 控制項相關的工作和增強功能的類型：  
  
-   [最佳化 ActiveX 控制項](../../mfc/mfc-activex-controls-optimization.md)  
  
-   [將內建事件加入至 ActiveX 控制項](../../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md)  
  
-   [加入自訂事件](../../mfc/mfc-activex-controls-adding-custom-events.md)  
  
-   [加入內建方法](../../mfc/mfc-activex-controls-adding-stock-methods.md)  
  
-   [加入自訂方法](../../mfc/mfc-activex-controls-adding-custom-methods.md)  
  
-   [加入內建屬性](../../mfc/mfc-activex-controls-adding-stock-properties.md)  
  
-   [加入自訂屬性](../../mfc/mfc-activex-controls-adding-custom-properties.md)  
  
-   [在 ActiveX 控制項容器中程式設計 ActiveX 控制項](../../mfc/programming-activex-controls-in-a-activex-control-container.md)  
  
## 概觀  
 這個精靈頁面將會為您建立的 MFC ActiveX 控制項專案描述目前的應用程式設定。  在預設情況下，精靈會如下建立專案：  
  
-   預設專案不會產生執行階段授權或說明檔。  您可在[應用程式設定](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)頁面變更這些預設值。  只有在 ActiveX 控制項精靈的這個頁面上所進行的選取會反映在 \[概觀\] 頁面中。  
  
-   專案會根據專案的名稱來包含控制項類別和屬性頁類別。  您可以在[控制項名稱](../../mfc/reference/control-names-mfc-activex-control-wizard.md)頁面上編輯專案的名稱和檔名。  
  
-   控制項並不是以現有的 Windows 控制項為基礎、而是在可見時啟動、具有使用者介面且包含 \[**關於**\] 對話方塊。  您可在[控制項設定](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)頁面變更這些預設值。  
  
## 請參閱  
 [建立和管理 Visual C\+\+ 專案](../../ide/creating-and-managing-visual-cpp-projects.md)   
 [Visual C\+\+ 專案類型](../../ide/visual-cpp-project-types.md)   
 [概念](../../atl/active-template-library-atl-concepts.md)