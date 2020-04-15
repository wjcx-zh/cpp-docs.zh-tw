---
title: 如何：新增命令傳送至 Windows Form 控制項
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- command routing [C++], adding to Windows Forms controls
- Windows Forms controls [C++], command routing
ms.assetid: bf138ece-b463-442a-b0a0-de7063a760c0
ms.openlocfilehash: ad64a12051c22a0cfca99d3ec9c5abef579902f4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365162"
---
# <a name="how-to-add-command-routing-to-the-windows-forms-control"></a>如何：新增命令傳送至 Windows Form 控制項

[CWinFormsView](../mfc/reference/cwinformsview-class.md)將指令和更新命令 UI 消息路由到使用者控制項,以允許它處理 MFC 命令(例如,框架功能表項和工具列按鈕)。

使用者控制項使用[ICommandTarget::初始化](../mfc/reference/icommandtarget-interface.md#initialize)來儲存對 命令來源`m_CmdSrc`物件的引用,如以下範例所示。 要使用`ICommandTarget`,必須添加對 mfcmifc80.dll 的引用。

`CWinFormsView`通過將多個常見的 MFC 檢視通知轉發到託管使用者控件來處理它們。 這些通知包括[「初始更新](../mfc/reference/iview-interface.md#oninitialupdate)[」、「更新」](../mfc/reference/iview-interface.md#onupdate)和[「啟動檢視」](../mfc/reference/iview-interface.md#onactivateview)方法。

這個主題假定您以前已完成[了「如何操作:在對話框中建立使用者控制和主機](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)[」以及如何:建立使用者控制和主機 MDI 檢視](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)。

### <a name="to-create-the-mfc-host-application"></a>建立 MFC 主機應用程式

1. 開啟您在「如何操作」 中建立的 Windows 窗體控制件庫[:在對話框中建立使用者控制件和主機](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)。

1. 新增對 mfcmifc80.dll 的引用,您可以通過右鍵單擊**解決方案資源管理器**中的專案節點,選擇 **"添加**",**參考**,然後流覽到 Microsoft Visual Studio 10.0_VC_atlmfc_lib。

1. 開啟UserControl1.Designer.cs並添加以下使用語句:

    ```
    using Microsoft.VisualC.MFC;
    ```

1. 此外,在UserControl1.Designer.cs中,更改此行:

    ```
    partial class UserControl1
    ```

   變更為以下程式碼：

    ```
    partial class UserControl1 : System.Windows.Forms.UserControl, ICommandTarget
    ```

1. 將新增為`UserControl1`的類別定義的第一行:

    ```
    private ICommandSource m_CmdSrc;
    ```

1. 將以下方法定義加入`UserControl1`(我們將在下一步中建立 MFC 控制件的 ID):

    ```
    public void Initialize (ICommandSource cmdSrc)
    {
       m_CmdSrc = cmdSrc;
       // need ID of control in MFC dialog and callback function
       m_CmdSrc.AddCommandHandler(32771, new CommandHandler (singleMenuHandler));
    }

    private void singleMenuHandler (uint cmdUI)
    {
       // User command handler code
       System.Windows.Forms.MessageBox.Show("Custom menu option was clicked.");
    }
    ```

1. 開啟您在[「如何建立」 的 MFC 應用程式:建立使用者控制和主機 MDI 檢視](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)。

1. 添加將調用`singleMenuHandler`的功能表選項。

   跳到**資源檢視**(Ctrl_Shift_E),展開**選單**資料夾,然後按兩下**IDR_MFC02TYPE**。 這將顯示功能表編輯器。

   在 **「檢視」** 選單底部添加功能表選項。 請注意「**屬性」** 視窗中選單選項的 ID。 儲存檔案。

   在**解決方案資源管理員**中,打開 Resource.h 檔,複製剛剛新增的選單選項的 ID 值,並將該值`m_CmdSrc.AddCommandHandler`作為第一個參數貼上`Initialize`C#`32771`專案方法中的呼叫( 如有必要取代)。

1. 建置並執行專案。

   在 [建置]**** 功能表上，按一下 [建置方案]****。

   在 **「調試」** 選單上,按一下 **「 不調試即可開始**」。

   選擇您添加的功能表選項。 請注意,調用 .dll 中的方法。

## <a name="see-also"></a>另請參閱

[將 Windows Form 使用者控制項裝載為 MFC 檢視](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[ICommandSource 介面](../mfc/reference/icommandsource-interface.md)<br/>
[ICommandTarget 介面](../mfc/reference/icommandtarget-interface.md)
