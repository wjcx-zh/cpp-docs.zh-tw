---
title: 如何： 新增命令傳送至 Windows Form 控制項 |Microsoft 文件
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- command routing [C++], adding to Windows Forms controls
- Windows Forms controls [C++], command routing
ms.assetid: bf138ece-b463-442a-b0a0-de7063a760c0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4c13b0bedf7c81431449aaed8d4fa8f067cdf3d9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33133645"
---
# <a name="how-to-add-command-routing-to-the-windows-forms-control"></a>如何：新增命令傳送至 Windows Form 控制項
[CWinFormsView](../mfc/reference/cwinformsview-class.md)將命令和更新命令 UI 訊息路由傳送至使用者控制項，允許它處理 MFC 命令 （例如，框架功能表項目和工具列按鈕）。  
  
 使用者控制項使用[ICommandTarget::Initialize](../mfc/reference/icommandtarget-interface.md#initialize)儲存中的命令來源物件的參考`m_CmdSrc`，如下列範例所示。 若要使用`ICommandTarget`您必須加入 mfcmifc80.dll 的參考。  
  
 `CWinFormsView` 處理數個常見的 MFC 檢視通知轉寄給受管理的使用者控制項。 這些通知包含[OnInitialUpdate](../mfc/reference/iview-interface.md#oninitialupdate)， [OnUpdate](../mfc/reference/iview-interface.md#onupdate)和[OnActivateView](../mfc/reference/iview-interface.md#onactivateview)方法。  
  
 本主題假設您之前已經完成[How to： 在對話方塊中建立使用者控制項並裝載](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)和[How to： 建立使用者控制項和主應用程式 MDI 檢視](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)。  
  
### <a name="to-create-the-mfc-host-application"></a>若要建立 MFC 主應用程式  
  
1.  開啟 Windows Form 控制項程式庫中建立[How to： 在對話方塊中建立使用者控制項並裝載](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)。  
  
2.  將參考加入 mfcmifc80.dll，您可以以滑鼠右鍵按一下專案節點中的**方案總管 中**、 選取**新增**，**參考**，然後瀏覽至Microsoft Visual Studio 10.0\VC\atlmfc\lib。  
  
3.  開啟 UserControl1.Designer.cs 並加入下列 using 陳述式：  
  
    ```  
    using Microsoft.VisualC.MFC;  
    ```  
  
4.  此外，在 UserControl1.Designer.cs，來變更這一行：  
  
    ```  
    partial class UserControl1  
    ```  
  
     為此值：  
  
    ```  
    partial class UserControl1 : System.Windows.Forms.UserControl, ICommandTarget  
    ```  
  
5.  將下列類別定義的第一行`UserControl1`:  
  
    ```  
    private ICommandSource m_CmdSrc;  
    ```  
  
6.  加入下列方法定義，以便`UserControl1`（我們將在下一個步驟建立 MFC 控制項的 ID）：  
  
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
  
7.  開啟您在建立 MFC 應用程式[How to： 建立使用者控制項和主應用程式 MDI 檢視](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)。  
  
8.  加入功能表選項將會叫用`singleMenuHandler`。  
  
     移至**資源檢視**(Ctrl + Shift + E)，依序展開**功能表**資料夾，然後再按兩下**IDR_MFC02TYPE**。 這會顯示功能表編輯器。  
  
     加入功能表選項底部**檢視**功能表。 請注意功能表選項中的識別碼**屬性**視窗。 儲存檔案。  
  
     在**方案總管 中**、 開啟 Resource.h 檔案，複製您剛才加入的功能表選項的識別碼值並貼上的第一個參數的值`m_CmdSrc.AddCommandHandler`C# 專案中呼叫`Initialize`（取代方法`32771`如有必要)。  
  
9. 建置並執行專案。  
  
     在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。  
  
     在**偵錯**功能表上，按一下 **啟動但不偵錯**。  
  
     選取您加入的功能表選項。 請注意，會呼叫此.dll 檔中的方法。  
  
## <a name="see-also"></a>另請參閱  
 [Windows Form 使用者控制項裝載為 MFC 檢視](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)   
 [ICommandSource 介面](../mfc/reference/icommandsource-interface.md)   
 [ICommandTarget 介面](../mfc/reference/icommandtarget-interface.md)   
 [CommandHandler](http://msdn.microsoft.com/Library/22096734-e074-4aca-8523-4b15590109f9)