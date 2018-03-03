---
title: "從類型程式庫加入 MFC 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- classes [MFC], adding MFC
- MFC, adding classes from type libraries
- type libraries, adding MFC classes from
ms.assetid: aba40476-3cfb-47af-990e-ae2e9e0d79cf
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1efc61e097d7e1136fdb7b6ef740dc00342077e4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="adding-an-mfc-class-from-a-type-library"></a>從類型程式庫加入 MFC 類別
使用此精靈，從可用的型別程式庫中的介面建立的 MFC 類別。 您可以加入至 MFC 類別[MFC 應用程式](../../mfc/reference/creating-an-mfc-application.md)、 [MFC DLL](../../mfc/reference/creating-an-mfc-dll-project.md)，或[MFC ActiveX 控制項](../../mfc/reference/creating-an-mfc-activex-control.md)。  
  
> [!NOTE]
>  您不需要啟用，以將類別從類型程式庫的自動化來建立 MFC 專案。  
  
 類型程式庫包含元件，請定義的方法，以及它們的參數和傳回型別所公開之介面的二進位描述。 必須針對出現在註冊類型程式庫**可用的型別程式庫**Typelib 精靈的加入類別中的清單。 請參閱 < 內分散式 COM:: 類型程式庫和語言整合"在 MSDN library，如需詳細資訊。  
  
### <a name="to-add-an-mfc-class-from-a-type-library"></a>若要從類型程式庫加入 MFC 類別  
  
1.  在**方案總管 中**或[類別檢視](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925)，以滑鼠右鍵按一下您要將類別加入的專案的名稱。  
  
2.  從捷徑功能表，按一下 **新增**，然後按一下 **加入類別**。  
  
3.  在[加入類別](../../ide/add-class-dialog-box.md)對話方塊，在 [範本] 窗格中，按一下**Typelib 的 MFC 類別**，然後按一下 **開啟**顯示[從 Typelib 精靈的 加入類別](../../mfc/reference/add-class-from-typelib-wizard.md).  
  
 在精靈中，您可以加入多個類型程式庫中的類別。 同樣地，您可以在單一精靈工作階段中，從一個以上的類型程式庫加入類別。  
  
 精靈會建立 MFC 類別，衍生自[COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md)，為您從選取的類型程式庫加入每個介面。 `COleDispatchDriver`實作 OLE automation 的用戶端。  
  
## <a name="see-also"></a>請參閱  
 [Automation 用戶端](../../mfc/automation-clients.md)   
 [Automation 用戶端：使用型別程式庫](../../mfc/automation-clients-using-type-libraries.md)

