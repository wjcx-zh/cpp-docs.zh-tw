---
title: "編輯 COM 介面 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.codewiz.com.editing.interfaces
dev_langs:
- C++
helpviewer_keywords:
- methods [C++], adding to COM interfaces
- COM interfaces, editing
- properties [C++], adding to COM interfaces
ms.assetid: 6c2909e0-af2d-4a37-bb39-ed372e6129cf
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b8911f23ce8e28f2da13c3d8305f4f13a861bb60
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="editing-a-com-interface"></a>編輯 COM 介面
使用類別檢視捷徑功能表的命令，您可以在 Visual c + + 專案中定義新方法和屬性的 COM 介面。 此外，從 [工具箱] 中，您可以定義 ActiveX 控制項的事件。  
  
 ATL 和 MFC 架構 COM 物件的類別，您可以編輯您編輯介面，同時在類別實作。  
  
> [!NOTE]
>  您所定義的外部介面**加入類別**對話方塊中，Visual c + + 會將方法或屬性新增至.idl 檔案，並加入類別可實作方法，即使介面手動新增虛設常式。  
  
 下列三個精靈可協助您自訂現有的介面。 這些屬性可從類別檢視：  
  
|精靈|專案類型|  
|------------|------------------|  
|[加入屬性精靈](../ide/names-add-property-wizard.md)|支援打破 ATL 或 MFC 專案 以滑鼠右鍵按一下您要加入屬性的介面。<br /><br /> Visual c + + 會偵測專案類型，並據此修改加入屬性精靈 中的選項：<br /><br /> -若為使用所建立的專案中的分配介面[MFC 應用程式精靈](../mfc/reference/mfc-application-wizard.md)，叫用 [加入屬性精靈] 提供 MFC 特有的選項。<br />-若為 MFC ActiveX 控制項的介面，加入屬性精靈 會提供內建的方法和屬性，您可以使用所提供或自訂控制項的清單。<br />-若為所有其他的介面，加入屬性精靈會提供在大部分情況下有用的選項。|  
|[新增方法精靈](../ide/add-method-wizard.md)|支援打破 ATL 或 MFC 專案 以滑鼠右鍵按一下您要將方法的介面。<br /><br /> Visual c + + 會偵測專案類型，並據此修改加入方法精靈中的選項：<br /><br /> -若為使用所建立的專案中的分配介面[MFC 應用程式精靈](../mfc/reference/mfc-application-wizard.md)，叫用加入方法精靈提供 MFC 特有的選項。<br />-若為 MFC ActiveX 控制項的介面，加入方法精靈會提供內建的方法和屬性，您可以使用所提供或自訂控制項的清單。<br />-若為所有其他的介面，**加入方法**精靈將會提供在大部分情況下有用的選項。|  
  
 此外，實作新介面 COM 控制項上按一下滑鼠右鍵在 類別檢視物件的控制項類別，[實作介面](../ide/implement-interface-wizard.md)。  
  
## <a name="see-also"></a>請參閱  
 [使用資源檔](../windows/working-with-resource-files.md)   
 [使用程式碼精靈加入功能](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Visual C++ 專案類型](../ide/visual-cpp-project-types.md)