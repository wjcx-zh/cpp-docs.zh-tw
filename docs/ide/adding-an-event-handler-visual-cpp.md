---
title: "加入事件處理常式 （Visual c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.eventhandler.overview
dev_langs: C++
helpviewer_keywords:
- event handlers, adding
- properties [Visual Studio], MSBuild
- MSBuild, properties
ms.assetid: 050bebf0-a9e0-474b-905c-796fe5ac8fc3
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f9a5380bf335a13bbf7b2f54840c9d1160187167
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="adding-an-event-handler-visual-c"></a>加入事件處理常式 (Visual C++)
在資源編輯器中，您可以加入新的事件處理常式，或編輯現有事件處理常式，如對話方塊方塊控制項使用[事件處理常式精靈](../ide/event-handler-wizard.md)。  
  
 您可以加入實作對話方塊方塊中使用的類別中的事件[屬性 視窗](/visualstudio/ide/reference/properties-window)。 如果您想要將事件加入至對話方塊類別以外的類別，請使用 事件處理常式精靈。  
  
### <a name="to-add-an-event-handler-to-a-dialog-box-control"></a>若要將事件處理常式加入至對話方塊控制項  
  
1.  按兩下在對話方塊資源[資源檢視](../windows/resource-view-window.md)開啟包含控制項中的對話方塊資源[對話方塊編輯器](../windows/dialog-editor.md)。  
  
2.  以滑鼠右鍵按一下您想要處理通知事件的控制項。  
  
3.  在捷徑功能表，按一下 **加入事件處理常式**以顯示事件處理常式精靈。  
  
4.  選取的事件中**訊息類型**方塊將新增至在所選取的類別**類別清單**方塊。  
  
5.  接受預設名稱在**函式的處理常式名稱**方塊中，或提供您選擇的名稱。  
  
6.  按一下**加入並編輯**加入專案中的事件處理常式並開啟新的函式在文字編輯器，加入適當的事件處理常式程式碼。  
  
     如果選取的訊息類型已經有選取的類別，事件處理常式**加入並編輯**無法使用，和**編輯程式碼**可用。 按一下**編輯程式碼**在現有的函式在文字編輯器開啟。  
  
 或者，您可以在其中加入事件處理常式從[屬性 視窗](/visualstudio/ide/reference/properties-window)。 請參閱[加入對話方塊控制項的事件處理常式](../windows/adding-event-handlers-for-dialog-box-controls.md)如需詳細資訊。  
  
## <a name="see-also"></a>請參閱  
 [使用程式碼精靈加入功能](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [加入類別](../ide/adding-a-class-visual-cpp.md)   
 [加入成員變數](../ide/adding-a-member-variable-visual-cpp.md)   
 [加入成員函式](../ide/adding-a-member-function-visual-cpp.md)   
 [MFC 訊息處理常式](../mfc/reference/adding-an-mfc-message-handler.md)   
 [巡覽類別結構](../ide/navigating-the-class-structure-visual-cpp.md)