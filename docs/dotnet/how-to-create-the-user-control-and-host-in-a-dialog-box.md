---
title: HOW TO：在對話方塊中建立使用者控制項並裝載
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], hosting a Windows Forms Control
- Windows Forms [C++], MFC support
ms.assetid: 03a53032-2f03-4fa2-b567-031615a26011
ms.openlocfilehash: bdf7e2f4961a16e6538c7bbcc690ef44ba87fcaf
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57751488"
---
# <a name="how-to-create-the-user-control-and-host-in-a-dialog-box"></a>HOW TO：在對話方塊中建立使用者控制項並裝載

這篇文章中的步驟假設您要建立對話方塊架構 ([CDialog 類別](../mfc/reference/cdialog-class.md)) Microsoft Foundation Classes (MFC) 專案，但是您也可以將支援的 Windows Form 控制項加入至現有的 MFC 對話方塊。

### <a name="to-create-the-net-user-control"></a>若要建立.NET 使用者控制項

1. 建立 Visual C# Windows Form 控制項程式庫專案，名為`WindowsFormsControlLibrary1`。

   在 [檔案]  功能表上，按一下 [新增]  及 [專案] 。 在  **Visual C#** 資料夾中，選取**Windows Forms 控制項程式庫**。

   接受`WindowsFormsControlLibrary1`專案名稱，依序按一下 **[確定]**。

   根據預設，.NET 控制項的名稱會是`UserControl1`。

1. 加入子控制項`UserControl1`。

   在 **工具箱**，開啟**所有的 Windows Form**清單。 拖曳** 按鈕**若要控制`UserControl1`設計介面。

   也加入**TextBox**控制項。

1. 在 **方案總管**，按兩下**UserControl1.Designer.cs**以開啟它進行編輯。 變更文字方塊和按鈕的宣告`private`至`public`。

1. 建置專案。

   在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。

### <a name="to-create-the-mfc-host-application"></a>若要建立 MFC 主應用程式

1. 建立 MFC 應用程式專案。

   在 [檔案]  功能表上，按一下 [新增]  及 [專案] 。 在  **Visual c + +** 資料夾中，選取**MFC 應用程式**。

   在 [名稱]  方塊中，輸入 `MFC01`。 將方案設定變更為**加入至方案**。 按一下 [確定] 。

   在  **MFC 應用程式精靈**，針對應用程式類型，選取**採用對話方塊**。 接受其餘的預設設定，然後按**完成**。 這會建立具有 MFC 對話方塊的 MFC 應用程式。

1. MFC 對話方塊中，加入預留位置控制項。

   在 **檢視**功能表上，按一下**資源檢視**。 在 **資源檢視**，展開**對話方塊**資料夾，然後按兩下`IDD_MFC01_DIALOG`。 對話方塊資源隨即出現在**資源編輯器**。

   在 **工具箱**，開啟**對話方塊編輯器**清單。 拖曳**靜態文字**對話方塊資源的控制。 **靜態文字**控制項將會當做.NET Windows Forms 控制項的預留位置。 其大小調整為大約 Windows Form 控制項的大小。

   中**屬性**視窗中，變更**識別碼**的**靜態文字**若要控制`IDC_CTRL1`並變更**TabStop**屬性 **，則為 true**。

1. 設定專案的 Common Language Runtime (CLR) 支援。

   在 **方案總管**，以滑鼠右鍵按一下 MFC01 專案節點，然後按一下**屬性**。

   在 **屬性頁**對話方塊的 **組態屬性**，選取**一般**。 在 **專案預設值**區段中，將**Common Language Runtime 支援**來**Common Language Runtime 支援 (/ clr)**。

   底下**組態屬性**，展開**C/c + +** ，然後選取**一般**節點。 設定**偵錯資訊格式**要**程式資料庫 (/Zi)**。

   選取 **程式碼產生**節點。 設定**啟用最少重建**要**否 (/ /gm-)**。 Ssprop_param_table_default**基本執行階段會檢查**要**預設**。

   按一下 **確定**以套用變更。

1. 新增.NET 控制項的參考。

   在 **方案總管**，以滑鼠右鍵按一下 MFC01 專案節點，然後按一下**新增**，**參考**。 上**屬性頁**，按一下**加入新參考**，選取**WindowsFormsControlLibrary1** (下**專案** 索引標籤)，然後按一下**確定**。 這會將參考新增的形式[/FU](../build/reference/fu-name-forced-hash-using-file.md)編譯器選項，如此將會編譯程式。 它還可讓 WindowsFormsControlLibrary1.dll 的複本 \MFC01\ 專案資料夾中，讓程式得以執行。

1. 在 Stdafx.h 中尋找此行：

    ```
    #endif // _AFX_NO_AFXCMN_SUPPORT
    ```

   它的上方，新增下列行：

    ```
    #include <afxwinforms.h>   // MFC Windows Forms support
    ```

1. 加入建立 managed 的控制項的程式碼。

   首先，宣告 managed 的控制項。 在 MFC01Dlg.h 中，移至對話方塊類別的宣告，在 Protected 範圍內，加入使用者控制項的資料成員時，也將，如下所示。

    ```
    class CMFC01Dlg : public CDialog
    {
       // ...
       // Data member for the .NET User Control:
       CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_ctrl1;
    ```

   接下來，提供 managed 控制項的實作。 在 mfc01dlg.cpp 內，在對話方塊中的覆寫`CMFC01Dlg::DoDataExchange`MFC 應用程式精靈所產生 (不`CAboutDlg::DoDataExchange`，這是在相同的檔案)，新增下列程式碼，建立 managed 的控制項，並將它與靜態的預留位置 IDC_CTRL1 產生關聯。

    ```
    void CMFC01Dlg::DoDataExchange(CDataExchange* pDX)
    {
       CDialog::DoDataExchange(pDX);
       DDX_ManagedControl(pDX, IDC_CTRL1, m_ctrl1);
    }
    ```

1. 建置並執行專案。

   在 **方案總管**，以滑鼠右鍵按一下**MFC01** ，然後按一下 **設定為啟始專案**。

   在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。

   在 **偵錯**功能表上，按一下**啟動但不偵錯**。 在 MFC 對話方塊中應該會顯示在 Windows Form 控制項。

## <a name="see-also"></a>另請參閱

[將 Windows Forms 使用者控制項裝載至 MFC 對話方塊中](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)
