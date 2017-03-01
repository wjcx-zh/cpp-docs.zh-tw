---
title: "MFC ActiveX 控制項精靈 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.appwiz.mfc.ctl.overview
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [C++], MFC
- MFC ActiveX controls [C++], wizards
- OLE controls [C++], creating
- MFC ActiveX Control Wizard
- OLE controls [C++]
ms.assetid: f19d698c-bdc3-4c74-af97-3d6ccb441b75
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 734c8dfdef42a0de614e02197d8cefdf4adc1bf1
ms.lasthandoff: 02/24/2017

---
# <a name="mfc-activex-control-wizard"></a>MFC ActiveX 控制項精靈
ActiveX 控制項是特定類型的[automation 伺服程式](../../mfc/automation-servers.md); 它是一個可重複使用的元件。 裝載 ActiveX 控制項的應用程式是[automation 用戶端](../../mfc/automation-clients.md)該控制項。 如果您的目標是要建立可重複使用元件，然後使用這個精靈來建立您的控制項。 請參閱[MFC ActiveX 控制項](../../mfc/mfc-activex-controls.md)如需詳細資訊。  
  
 或者，您可以建立自動化伺服器 MFC 應用程式使用[MFC 應用程式精靈](../../mfc/reference/mfc-application-wizard.md)。  
  
 使用此精靈建立 ActiveX 控制項可以具有使用者介面，或可以是不可見。 您可以指定此選項在[控制設定](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)精靈中的頁面。 Timer 控制項是您想要看不見的 ActiveX 控制項的範例。  
  
 ActiveX 控制項可以有複雜的使用者介面。 某些控制項可能會像封裝的表單︰ 單一控制項包含許多欄位，每個 Windows 控制項本身。 比方說，實作為 MFC ActiveX 控制項的自動部分物件可能會顯示類似表單的使用者介面，讓使用者可讀取，並編輯零件編號、 組件名稱和其他資訊。 請參閱[MFC ActiveX 控制項](../../mfc/mfc-activex-controls.md)如需詳細資訊。  
  
 如果您需要建立 ActiveX 物件的容器，請參閱[建立 ActiveX 控制項容器](../../mfc/reference/creating-an-mfc-activex-control-container.md)。  
  
 MFC 起始程式包括 c + + 原始程式 (.cpp) 檔、 資源 (.rc) 檔案和專案 (.vcxproj) 檔案。 起始檔案中產生的程式碼是以 MFC 為基礎。  
  
 下面範例會顯示工作和增強功能，為您的 ActiveX 控制項的類型︰  
  
-   [最佳化 ActiveX 控制項](../../mfc/mfc-activex-controls-optimization.md)  
  
-   [內建事件加入至 ActiveX 控制項](../../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md)  
  
-   [加入自訂事件](../../mfc/mfc-activex-controls-adding-custom-events.md)  
  
-   [加入內建方法](../../mfc/mfc-activex-controls-adding-stock-methods.md)  
  
-   [加入自訂方法](../../mfc/mfc-activex-controls-adding-custom-methods.md)  
  
-   [加入內建屬性](../../mfc/mfc-activex-controls-adding-stock-properties.md)  
  
-   [加入自訂屬性](../../mfc/mfc-activex-controls-adding-custom-properties.md)  
  
-   [ActiveX 控制項容器中程式設計 ActiveX 控制項](../../mfc/programming-activex-controls-in-a-activex-control-container.md)  
  
## <a name="overview"></a>概觀  
 此精靈頁面說明您要建立 MFC ActiveX 控制項專案的目前應用程式設定。 依預設，此精靈建立專案，如下所示︰  
  
-   預設專案會產生任何執行階段授權或說明檔。 您可以變更這些預設設定上[應用程式設定](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)頁面。 只有您進行 ActiveX 控制項精靈的這個頁面的選取會反映在**概觀**頁面。  
  
-   專案會包含控制項類別和屬性頁類別，根據專案的名稱。 您可以編輯您的專案和檔案名稱上[控制項名稱](../../mfc/reference/control-names-mfc-activex-control-wizard.md)頁面。  
  
-   控制項沒有現有的 Windows 控制項為基礎，它會成為可見狀態，具有使用者介面，並包含時啟動**有關**對話方塊。 您可以變更這些預設設定上[控制設定](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)頁面。  
  
## <a name="see-also"></a>另請參閱  
 [建立和管理 Visual c + + 專案](../../ide/creating-and-managing-visual-cpp-projects.md)   
 [Visual c + + 專案類型](../../ide/visual-cpp-project-types.md)   
 [概念](../../atl/active-template-library-atl-concepts.md)


