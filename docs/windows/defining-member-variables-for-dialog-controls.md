---
title: "定義對話方塊控制項的成員變數 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- member variables, defining for controls
- variables, dialog box control member variables
- controls [C++], member variables
- Dialog editor, defining member variables for controls
ms.assetid: 84347c63-c33c-4b04-91f5-6d008c45ba58
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: eb966459695eb048943a12e33c8e909f99fdc92b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="defining-member-variables-for-dialog-controls"></a>定義對話方塊控制項的成員變數
若要定義任何對話方塊控制項 (按鈕除外) 的成員變數，您可以使用下列方法。  
  
> [!NOTE]
>  本文只適用於 MFC 專案內的對話方塊控制項。 ATL 專案應使用**新的 Windows 訊息和事件處理常式** 對話方塊。  
  
### <a name="to-define-a-member-variable-for-a-non-button-dialog-box-control"></a>定義對話方塊控制項的成員變數 (非按鈕)  
  
1.  在[對話方塊編輯器](../windows/dialog-editor.md)，選取控制項。  
  
2.  同時按**CTRL**機碼中，按兩下對話方塊控制項。  
  
     [加入成員變數精靈](../ide/add-member-variable-wizard.md)隨即出現。  
  
3.  輸入中的適當資訊**加入成員變數**精靈。 如需詳細資訊，請參閱[對話方塊資料交換](../mfc/dialog-data-exchange.md)。  
  
4.  按一下**確定**返回對話方塊編輯器。  
  
    > [!TIP]
    >  若要從任何對話方塊控制項跳至其現有的處理常式，請按兩下控制項。  
  

  
 您也可以使用**成員變數**索引標籤中**MFC 類別精靈**，新增新成員變數指定的類別，並檢視這些已定義。  
  
 需求  
  
 MFC  
  
## <a name="see-also"></a>請參閱  
 [將訊息對應到函式](../mfc/reference/mapping-messages-to-functions.md)   
 [使用程式碼精靈加入功能](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [MFC 類別精靈](../mfc/reference/mfc-class-wizard.md)   
 [加入類別](../ide/adding-a-class-visual-cpp.md)   
 [加入成員函式](../ide/adding-a-member-function-visual-cpp.md)   
 [加入成員變數](../ide/adding-a-member-variable-visual-cpp.md)   
 [覆寫虛擬函式](../ide/overriding-a-virtual-function-visual-cpp.md)   
 [MFC 訊息處理常式](../mfc/reference/adding-an-mfc-message-handler.md)

