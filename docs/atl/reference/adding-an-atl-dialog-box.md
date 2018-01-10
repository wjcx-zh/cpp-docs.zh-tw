---
title: "加入 ATL 對話方塊 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords:
- ATL projects, adding dialog resources
- MFC dialog boxes, ATL dialogs
- dialog boxes, ATL
ms.assetid: 152a378f-7b24-4f66-aeba-c740973f03a6
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d8c9969f4747c6c3fa2a39b7b0452f6ac54c9d58
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="adding-an-atl-dialog-box"></a>加入 ATL 對話方塊
若要將 ATL 對話方塊加入至您的專案，您的專案必須 ATL 專案或包含 ATL 支援的 MFC 專案。 您可以使用[ATL 專案精靈](../../atl/reference/atl-project-wizard.md)建立 ATL 應用程式，或[MFC 應用程式中加入 ATL 物件](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)實作 MFC 應用程式的 ATL 支援。  
  
 根據預設，ATL 對話方塊精靈可實作衍生自對話方塊[CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md)。 這個類別包含支援裝載 ActiveX 和 Windows 控制項。 如果您不要的額外負荷的 ActiveX 控制項支援之後在精靈產生程式碼,，取代所有的執行個體`CAxDialogImpl`其中一種[CSimpleDialog](../../atl/reference/csimpledialog-class.md)或[CDialogImpl](../../atl/reference/cdialogimpl-class.md)為您的基底類別.  
  
> [!NOTE]
>  `CSimpleDialog`建立支援 Windows 通用控制項的強制回應對話方塊方塊。 `CDialogImpl`建立任一獨佔式或非強制回應對話方塊。  
  
### <a name="to-add-an-atl-dialog-resource-to-your-project"></a>將 ATL 對話方塊資源新增至您的專案  
  
1.  ATL 專案使用建立[ATL 專案精靈](../../atl/reference/atl-project-wizard.md)。  
  
2.  從[類別檢視](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925)，以滑鼠右鍵按一下專案名稱，然後按一下**新增**從捷徑功能表。 按一下**加入類別**。  
  
3.  在範本窗格中[加入類別](../../ide/add-class-dialog-box.md)對話方塊中，按一下  **ATL 對話方塊**。 按一下**開啟**顯示[ATL 對話方塊精靈](../../atl/reference/atl-dialog-wizard.md)。  
  
 如需詳細資訊，請參閱[實作對話方塊](../../atl/implementing-a-dialog-box.md)。  
  
## <a name="see-also"></a>請參閱  
 [加入類別](../../ide/adding-a-class-visual-cpp.md)   
 [視窗類別](../../atl/atl-window-classes.md)   
 [訊息對應](../../atl/message-maps-atl.md)

