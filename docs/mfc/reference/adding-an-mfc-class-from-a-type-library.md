---
title: "從類型程式庫加入 MFC 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- classes [C++], adding MFC
- MFC, adding classes from type libraries
- type libraries, adding MFC classes from
ms.assetid: aba40476-3cfb-47af-990e-ae2e9e0d79cf
caps.latest.revision: 13
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
ms.openlocfilehash: 0aec2c2f83dcc5857134f39f6729ce1ca9aa1acf
ms.lasthandoff: 02/24/2017

---
# <a name="adding-an-mfc-class-from-a-type-library"></a>從類型程式庫加入 MFC 類別
使用此精靈建立的 MFC 類別會從可用的型別程式庫中的介面。 您可以加入至 MFC 類別[MFC 應用程式](../../mfc/reference/creating-an-mfc-application.md)、 [MFC DLL](../../mfc/reference/creating-an-mfc-dll-project.md)，或[MFC ActiveX 控制項](../../mfc/reference/creating-an-mfc-activex-control.md)。  
  
> [!NOTE]
>  您不需要從類型程式庫加入類別啟用自動化以建立您的 MFC 專案。  
  
 型別程式庫包含元件，請定義以及其參數和傳回型別方法所公開的介面的二進位的描述。 您必須針對才會出現在註冊您的型別程式庫**可用的型別程式庫**Typelib 精靈的加入類別中的清單。 請參閱 「 在分散式 COM:: 類型程式庫和語言整合 」，如需詳細資訊的 MSDN library 中。  
  
### <a name="to-add-an-mfc-class-from-a-type-library"></a>若要從型別程式庫加入 MFC 類別  
  
1.  在**方案總管 中**或[類別檢視](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925)，以滑鼠右鍵按一下您要將類別加入的專案的名稱。  
  
2.  從捷徑功能表，按一下 **新增**，然後按一下 **加入類別**。  
  
3.  在[加入類別](../../ide/add-class-dialog-box.md)對話方塊，在 [範本] 窗格中，按一下**從型別程式庫的 MFC 類別**，然後按一下 **開啟**顯示[Typelib 精靈的加入類別](../../mfc/reference/add-class-from-typelib-wizard.md)。  
  
 在精靈中，您可以加入多個類型程式庫中的類別。 同樣地，您可以從一個以上的型別程式庫加入類別，在單一精靈工作階段。  
  
 精靈會建立衍生自 MFC 類別[COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md)，為您從選取的類型程式庫加入每個介面。 `COleDispatchDriver`實作 OLE automation 用戶端。  
  
## <a name="see-also"></a>另請參閱  
 [Automation 用戶端](../../mfc/automation-clients.md)   
 [Automation 用戶端︰ 使用類型程式庫](../../mfc/automation-clients-using-type-libraries.md)


