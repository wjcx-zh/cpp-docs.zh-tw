---
title: 範例：透過功能表命令顯示對話方塊
ms.date: 09/07/2019
helpviewer_keywords:
- MFC dialog boxes [MFC], examples
- MFC dialog boxes [MFC], displaying
- modeless dialog boxes [MFC], displaying
- dialog boxes [MFC], MFC
- modal dialog boxes [MFC], displaying
- examples [MFC], dialog boxes
- menu items [MFC], examples
ms.assetid: e8692549-acd7-478f-9c5e-ba310ce8cccd
ms.openlocfilehash: 1cada8124cd7ea71a24367626508782b522cc746
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506760"
---
# <a name="example-displaying-a-dialog-box-via-a-menu-command"></a>範例：透過功能表命令顯示對話方塊

本主題包含下列程式：

- 透過功能表命令顯示模式對話方塊。

- 透過功能表命令顯示非強制回應對話方塊。

這兩個範例程式都適用于 MFC 應用程式，並可在您使用 [MFC 應用程式精靈](reference/mfc-application-wizard.md)所建立的應用程式中運作。

這些程式會使用下列名稱和值：

|項目|名稱或值|
|----------|-------------------|
|應用程式|DisplayDialog|
|功能表命令|[View] 功能表上的 [測試] 命令;命令識別碼 = ID_VIEW_TEST|
|對話方塊|測試對話方塊;Class = CTestDialog;標頭檔 = TestDialog .h;Variable = testdlg，ptestdlg|
|命令處理常式|OnViewTest|

### <a name="to-display-a-modal-dialog-box"></a>若要顯示模式對話方塊

1. 建立功能表命令;請參閱 [建立功能表或功能表項目](../windows/menu-editor.md)。

1. 建立對話方塊;請參閱 [啟動對話方塊編輯器](../windows/creating-a-new-dialog-box.md)。

1. 加入對話方塊的類別。 如需詳細資訊，請參閱 [新增類別](../ide/adding-a-class-visual-cpp.md) 。

1. 在 **類別檢視**中，選取 (CDisplayDialogDoc) 的檔類別。 在 [屬性]**** 視窗中，按一下 [事件]**** 按鈕。 按兩下功能表命令的識別碼 (ID_VIEW_TEST) 。 接著，按一下向下箭號，然後選取 [ ** \<Add> OnViewTest**]。

   如果您將功能表命令加入至 MDI 應用程式的大型主機，請改為選取應用程式類別 (CDisplayDialogApp) 。

1. 在現有的 include 語句之後，將下列 include 語句新增至 CDisplayDialogDoc .cpp (或 CDisplayDialogApp) .cpp：

   ```cpp
   #include "TestDialog.h"
   ```

1. 將下列程式碼加入至 `OnViewTest` 來執行函式：

   ```cpp
   CTestDialog testdlg;
   testdlg.DoModal();
   ```

### <a name="to-display-a-modeless-dialog-box"></a>若要顯示非強制回應對話方塊

1. 執行前四個步驟來顯示模式對話方塊，但在步驟4中選取 view 類別 (CDisplayDialogView) 除外。

1. 編輯 DisplayDialogView .h：

   - 宣告第一個類別宣告前面的對話方塊類別：

   ```cpp
   class CTestDialog;
   ```

   - 在屬性 public 區段之後，宣告指向對話方塊的指標：

   ```cpp
   CTestDialog* m_pTestDlg;
   ```

1. 編輯 DisplayDialogView .cpp：

   - 在現有的 include 語句之後，新增下列 include 語句：

   ```cpp
   #include "TestDialog.h"
   ```

   - 將下列程式碼新增至函式：

   ```cpp
   m_pTestDlg = NULL;
   ```

   - 將下列程式碼新增至函式：

   ```cpp
   delete m_pTestDlg;
   ```

   - 將下列程式碼加入至 `OnViewTest` 來執行函式：

   ```cpp
   if (NULL == m_pTestDlg)
   {
      m_pTestDlg = new CTestDialog(this);
      m_pTestDlg->Create(CTestDialog::IDD, this);
   }
   m_pTestDlg->ShowWindow(SW_SHOW);
   ```

## <a name="see-also"></a>另請參閱

[對話方塊](dialog-boxes.md)<br/>
[強制回應和非強制回應對話方塊](modal-and-modeless-dialog-boxes.md)
