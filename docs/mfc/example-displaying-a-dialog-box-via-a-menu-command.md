---
title: 範例： 透過功能表命令 對話方塊中顯示 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], examples
- MFC dialog boxes [MFC], displaying
- modeless dialog boxes [MFC], displaying
- dialog boxes [MFC], MFC
- modal dialog boxes [MFC], displaying
- examples [MFC], dialog boxes
- menu items [MFC], examples
ms.assetid: e8692549-acd7-478f-9c5e-ba310ce8cccd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 20d355215388861a7bc2586c2c253cd551124809
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="example-displaying-a-dialog-box-via-a-menu-command"></a>範例：透過功能表命令顯示對話方塊
本主題包含的程序：  
  
-   顯示強制回應對話方塊，透過功能表命令。  
  
-   顯示透過功能表命令的非強制回應對話方塊。  
  
 這兩個範例程序的 MFC 應用程式，而在您建立的應用程式中運作[MFC 應用程式精靈](../mfc/reference/mfc-application-wizard.md)。  
  
 這些程序使用下列名稱和值：  
  
|項目|名稱或值|  
|----------|-------------------|  
|應用程式|DisplayDialog|  
|功能表命令|測試檢視 功能表中; 上的命令命令 ID = ID_VIEW_TEST|  
|對話方塊|測試對話方塊。類別 = CTestDialog;標頭檔 = TestDialog.h;變數 = testdlg，ptestdlg|  
|命令處理常式|OnViewTest|  
  
### <a name="to-display-a-modal-dialog-box"></a>若要顯示強制回應對話方塊  
  
1.  建立功能表命令。請參閱[建立功能表或功能表項目](../windows/creating-a-menu.md)。  
  
2.  建立對話方塊。請參閱[啟動對話方塊編輯器](../windows/creating-a-new-dialog-box.md)。  
  
3.  新增您的對話方塊類別。 請參閱[將類別加入](../ide/adding-a-class-visual-cpp.md)如需詳細資訊。  
  
4.  在**類別檢視**，選取文件類別 (CDisplayDialogDoc)。 在 [屬性] 視窗中，按一下 [事件] 按鈕。 按兩下左窗格中的功能表命令 (ID_VIEW_TEST) 的識別碼**屬性**視窗，然後選取**命令**。 在右窗格中，按一下 向下箭號並選取**\<新增 > OnViewTest**。  
  
     如果您加入功能表命令到 MDI 應用程式的大型主機，請改為選取的應用程式類別 (CDisplayDialogApp)。  
  
5.  加入下列包含陳述式來 CDisplayDialogDoc.cpp （或 CDisplayDialogApp.cpp） 現有 include 陳述式之後：  
  
     [!code-cpp[NVC_MFCControlLadenDialog#42](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_1.cpp)]  
  
6.  將下列程式碼加入`OnViewTest`，實作函式：  
  
     [!code-cpp[NVC_MFCControlLadenDialog#43](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_2.cpp)]  
  
### <a name="to-display-a-modeless-dialog-box"></a>若要顯示非強制回應對話方塊  
  
1.  不要顯示強制回應對話方塊中，除了在步驟 4 中選取的檢視類別 (CDisplayDialogView) 的前四個步驟。  
  
2.  編輯 DisplayDialogView.h:  
  
    -   對話方塊類別宣告之前的第一個類別進行宣告：  
  
         [!code-cpp[NVC_MFCControlLadenDialog#44](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_3.h)]  
  
    -   屬性的公用區段之後宣告的指標 對話方塊：  
  
         [!code-cpp[NVC_MFCControlLadenDialog#45](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_4.h)]  
  
3.  編輯 DisplayDialogView.cpp:  
  
    -   加入下列包含陳述式之後現有 include 陳述式,：  
  
         [!code-cpp[NVC_MFCControlLadenDialog#42](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_1.cpp)]  
  
    -   將下列程式碼加入至建構函式：  
  
         [!code-cpp[NVC_MFCControlLadenDialog#46](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_5.cpp)]  
  
    -   解構函式中加入下列程式碼：  
  
         [!code-cpp[NVC_MFCControlLadenDialog#47](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_6.cpp)]  
  
    -   將下列程式碼加入`OnViewTest`，實作函式：  
  
         [!code-cpp[NVC_MFCControlLadenDialog#48](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_7.cpp)]  
  
 另請參閱下列知識庫文件：  
  
-   Q251059： 如何： 提供您自己的視窗類別名稱的 MFC 對話方塊  
  
## <a name="see-also"></a>另請參閱  
 [對話方塊](../mfc/dialog-boxes.md)   
 [強制回應和非強制回應對話方塊](../mfc/modal-and-modeless-dialog-boxes.md)

