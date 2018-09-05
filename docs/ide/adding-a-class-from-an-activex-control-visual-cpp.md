---
title: 從 ActiveX 控制項新增類別 (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [C++], adding classes
- classes [C++], creating
ms.assetid: 729fcb37-54b8-44d5-9b4e-50bb16e0eea4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b676e35dcf98ef7ae1f41e4a91922d689bd40409
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43202135"
---
# <a name="adding-a-class-from-an-activex-control-visual-c"></a>自 ActiveX 控制項加入類別 (Visual C++)
使用此精靈從可用 ActiveX 控制項中的介面建立 MFC 類別。 您可以將 MFC 類別新增至 [MFC 應用程式](../mfc/reference/creating-an-mfc-application.md)、[MFC DLL](../mfc/reference/creating-an-mfc-dll-project.md) 或 [MFC ActiveX 控制項](../mfc/reference/creating-an-mfc-activex-control.md)。  
  
> [!NOTE]
>  建立 MFC 專案時不需要啟用自動化，即可從 ActiveX 控制項新增類別。  
  
 ActiveX 控制項是可重複使用的軟體元件，以元件物件模型 (COM) 為基礎，支援各種不同的 OLE 功能並且可自訂以符合眾多軟體需求。 ActiveX 控制項的設計是要用於一般 ActiveX 控制項容器以及網際網路上的全球資訊網網頁。  
  
### <a name="to-add-an-mfc-class-from-an-activex-control"></a>從 ActiveX 控制項新增 MFC 類別  
  
1.  在 [方案總管] 或[類別檢視](https://msdn.microsoft.com/8d7430a9-3e33-454c-a9e1-a85e3d2db925)中，以滑鼠右鍵按一下您要將 ActiveX 控制項類別新增至其中的專案名稱。  
  
2.  從捷徑功能表按一下 [新增]，然後按一下 [新增類別]。  
  
3.  在[新增類別](../ide/add-class-dialog-box.md)對話方塊的 [範本] 窗格中，按一下 [來自 ActiveX 控制項的 MFC 類別]，然後按一下 [開啟]，顯示[從 ActiveX 控制項新增類別精靈](../ide/add-class-from-activex-control-wizard.md)。  
  
 在精靈中，您可以在 ActiveX 控制項中新增多個介面。 同樣地，您可以在單一精靈工作階段中，從多個 ActiveX 控制項建立類別。  
  
 您可以從系統中註冊的 ActiveX 控制項新增類別，或者可以從位於型別程式庫檔案 (.tlb、.olb、.dll、.ocx 或 .exe) 的 ActiveX 控制項新增類別，而不先在系統中註冊它們。 請參閱[註冊 OLE 控制項](../mfc/reference/registering-ole-controls.md)以取得註冊 ActiveX 控制項的詳細資訊。  
  
 精靈會為您從選取的 ActiveX 控制項新增的每個介面，建立 MFC 類別，類別會衍生自 [CWnd](../mfc/reference/cwnd-class.md) 或 [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)。  
  
## <a name="see-also"></a>請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   
 [COM 和 ATL 簡介](../atl/introduction-to-com-and-atl.md)