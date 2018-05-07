---
title: 將類別加入來自 ActiveX 控制項 （Visual c + +） |Microsoft 文件
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
ms.openlocfilehash: 793adf38da33808371a0df71f671c3e29da75326
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="adding-a-class-from-an-activex-control-visual-c"></a>自 ActiveX 控制項加入類別 (Visual C++)
使用此精靈建立的 MFC 類別與可用的 ActiveX 控制項的介面。 您可以加入至 MFC 類別[MFC 應用程式](../mfc/reference/creating-an-mfc-application.md)、 [MFC DLL](../mfc/reference/creating-an-mfc-dll-project.md)，或[MFC ActiveX 控制項](../mfc/reference/creating-an-mfc-activex-control.md)。  
  
> [!NOTE]
>  您不需要啟用，以將類別加入來自 ActiveX 控制項的自動化來建立 MFC 專案。  
  
 ActiveX 控制項是可重複使用的軟體元件為基礎的元件物件模型 (COM) 支援各種不同的 OLE 功能，並可自訂以符合多個軟體需求。 ActiveX 控制項的設計並適用於一般的 ActiveX 控制項容器中以及全球資訊網網頁在網際網路上。  
  
### <a name="to-add-an-mfc-class-from-an-activex-control"></a>若要加入來自 ActiveX 控制項的 MFC 類別  
  
1.  在**方案總管 中**或[類別檢視](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925)，以滑鼠右鍵按一下您要將 ActiveX 控制項類別加入的專案的名稱。  
  
2.  從捷徑功能表，按一下 **新增**，然後按一下 **加入類別**。  
  
3.  在[加入類別](../ide/add-class-dialog-box.md)對話方塊，在 [範本] 窗格中，按一下**來自 ActiveX 控制項的 MFC 類別**，然後按一下 **開啟**顯示[加入類別從 ActiveX精靈控制項](../ide/add-class-from-activex-control-wizard.md)。  
  
 在精靈中，您可以加入 ActiveX 控制項中的多個介面。 同樣地，您可以建立從多個 ActiveX 控制項的類別，在單一精靈工作階段中。  
  
 您可以從您的系統中註冊的 ActiveX 控制項加入類別，或您可以將類別加入來自 ActiveX 控制項位於不含第一個註冊您的系統中的類型程式庫檔案 （.tlb、.olb、.dll、.ocx 或.exe）。 請參閱[註冊 OLE 控制項](../mfc/reference/registering-ole-controls.md)如需有關註冊 ActiveX 控制項。  
  
 精靈會建立 MFC 類別，衍生自[CWnd](../mfc/reference/cwnd-class.md)或從[COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)，為您從選取的 ActiveX 控制項加入每個介面。  
  
## <a name="see-also"></a>另請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   
 [COM 和 ATL 簡介](../atl/introduction-to-com-and-atl.md)