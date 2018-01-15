---
title: "MFC ActiveX 控制項精靈 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.appwiz.mfc.ctl.overview
dev_langs: C++
helpviewer_keywords:
- ActiveX controls [MFC], MFC
- MFC ActiveX controls [MFC], wizards
- OLE controls [MFC], creating
- MFC ActiveX Control Wizard
- OLE controls [MFC]
ms.assetid: f19d698c-bdc3-4c74-af97-3d6ccb441b75
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 82e562ceb73da2b103360ab9607cecbbe9f1da02
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-control-wizard"></a>MFC ActiveX 控制項精靈
ActiveX 控制項是特定類型的[automation 伺服程式](../../mfc/automation-servers.md); 它是可重複使用的元件。 裝載 ActiveX 控制項的應用程式是[自動化用戶端](../../mfc/automation-clients.md)該控制項。 如果您的目標是建立可重複使用元件，然後使用這個精靈來建立您的控制項。 請參閱[MFC ActiveX 控制項](../../mfc/mfc-activex-controls.md)如需詳細資訊。  
  
 或者，您可以建立 automation 伺服器 MFC 應用程式使用[MFC 應用程式精靈](../../mfc/reference/mfc-application-wizard.md)。  
  
 使用此精靈建立 ActiveX 控制項可以包含使用者介面，或可以是不可見。 您可以指定這個選項在[控制設定](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)精靈中的頁面。 Timer 控制項是您要隱藏的 ActiveX 控制項的範例。  
  
 ActiveX 控制項可以有複雜的使用者介面。 某些控制項可能會像封裝的表單： 單一控制項包含許多欄位，每個 Windows 控制項，好似它本身。 例如，實作為 MFC ActiveX 控制項的自動部分物件可能會顯示類似表單的使用者介面，透過這些使用者無法讀取及編輯部分的數字、 組件名稱和其他資訊。 請參閱[MFC ActiveX 控制項](../../mfc/mfc-activex-controls.md)如需詳細資訊。  
  
 如果您需要建立 ActiveX 物件的容器，請參閱[建立 ActiveX 控制項容器](../../mfc/reference/creating-an-mfc-activex-control-container.md)。  
  
 MFC 入門程式包括 c + + 來源 (.cpp) 檔案、 資源 (.rc) 檔，以及專案 (.vcxproj) 檔案。 起始檔案中產生的程式碼是以 MFC 為基礎。  
  
 下面範例會顯示工作和類型的增強功能的 ActiveX 控制項：  
  
-   [最佳化 ActiveX 控制項](../../mfc/mfc-activex-controls-optimization.md)  
  
-   [將內建事件加入至 ActiveX 控制項](../../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md)  
  
-   [加入自訂事件](../../mfc/mfc-activex-controls-adding-custom-events.md)  
  
-   [加入內建方法](../../mfc/mfc-activex-controls-adding-stock-methods.md)  
  
-   [加入自訂方法](../../mfc/mfc-activex-controls-adding-custom-methods.md)  
  
-   [加入內建屬性](../../mfc/mfc-activex-controls-adding-stock-properties.md)  
  
-   [加入自訂屬性](../../mfc/mfc-activex-controls-adding-custom-properties.md)  
  
-   [ActiveX 控制項容器中程式設計 ActiveX 控制項](../../mfc/programming-activex-controls-in-a-activex-control-container.md)  
  
## <a name="overview"></a>總覽  
 這個精靈頁面說明目前的應用程式設定，您要建立 MFC ActiveX 控制項專案。 依預設，此精靈建立專案，如下所示：  
  
-   預設專案會產生任何執行階段授權或說明檔案。 您可以變更這些預設設定上[應用程式設定](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)頁面。 只將 ActiveX 控制項精靈的這個頁面所進行的選擇會反映在**概觀**頁面。  
  
-   專案會包含在控制項類別和屬性頁類別，根據專案的名稱。 您可以編輯您的專案和檔案名稱的名稱上[控制項名稱](../../mfc/reference/control-names-mfc-activex-control-wizard.md)頁面。  
  
-   控制項沒有現有的 Windows 控制項為基礎，啟動時，它會變成可見，具有使用者介面，並包含**有關**] 對話方塊。 您可以變更這些預設設定上[控制設定](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)頁面。  
  
## <a name="see-also"></a>請參閱  
 [建立和管理 Visual C++ 專案](../../ide/creating-and-managing-visual-cpp-projects.md)   
 [Visual c + + 專案類型](../../ide/visual-cpp-project-types.md)   
 [概念](../../atl/active-template-library-atl-concepts.md)

