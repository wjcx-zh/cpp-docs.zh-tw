---
title: 將 Windows Form 使用者控制項裝載成 MFC 對話方塊
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms [C++], hosting as MFC Dialog
- hosting Windows Forms control [C++]
ms.assetid: 0434a9d7-8b14-48e6-ad69-9ba9a684677a
ms.openlocfilehash: 1351f0b2aa4ebc288469231a27c691237b52b1c1
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2019
ms.locfileid: "73704132"
---
# <a name="hosting-a-windows-form-user-control-as-an-mfc-dialog-box"></a>將 Windows Form 使用者控制項裝載成 MFC 對話方塊

MFC 提供樣板類別[CWinFormsDialog](../mfc/reference/cwinformsdialog-class.md) ，讓您可以在強制回應或無模式 MFC 對話方塊中裝載 Windows Forms 使用者控制項（<xref:System.Windows.Forms.UserControl>）。 `CWinFormsDialog` 衍生自 MFC 類別[CDialog](../mfc/reference/cdialog-class.md)，因此可以將對話方塊啟動為強制回應或非強制回應。

`CWinFormsDialog` 用來裝載使用者控制項的程式，與在[MFC 對話方塊中裝載 Windows Form 使用者控制項](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)中所述的程式相同。 不過，`CWinFormsDialog` 會管理使用者控制項的初始化和裝載，使其不必以手動方式進行程式設計。

如需顯示與 MFC 搭配使用之 Windows Forms 的範例應用程式，請參閱[mfc 和 Windows Forms 整合](https://www.microsoft.com/en-us/download/details.aspx?id=2113)。

### <a name="to-create-the-mfc-host-application"></a>建立 MFC 主應用程式

1. 建立 MFC 應用程式專案。

   **在 [檔案**] 功能表上，選取 [**新增**]，然後按一下 [**專案**]。 在 [**視覺C++效果**] 資料夾中，選取 [ **MFC 應用程式**]。

   在 [**名稱**] 方塊中，輸入 `MFC03`，並將解決方案設定變更為 [**加入方案**]。按一下 **[確定]** 。

   在**MFC 應用程式精靈**中，接受所有預設值，然後按一下 **[完成]** 。 這會建立具有多個檔介面的 MFC 應用程式。

1. 設定專案。

   在**方案總管**中，以滑鼠右鍵按一下**MFC03**專案節點，然後選擇 [**屬性**]。 [**屬性頁**] 對話方塊隨即出現。

   在 [**屬性頁**] 對話方塊的 [設定**屬性**] 樹狀結構控制項中，選取 [**一般**]，然後在 [**專案預設值**] 區段中，將 [**通用語言執行時間支援**] 設定為 [ **common language runtime 支援] （/clr）** 。 按一下 [確定]。

1. 加入 .NET 控制項的參考。

   在**方案總管**中，以滑鼠右鍵按一下**MFC03**專案節點，然後選擇 [**加入**]、[**參考**]。 在**屬性頁**中，按一下 **[加入新參考**]，選取 [WindowsControlLibrary1] （在 [**專案**] 索引標籤下），然後按一下 **[確定]** 。 這會以[/FU](../build/reference/fu-name-forced-hash-using-file.md)編譯器選項的形式加入參考，讓程式進行編譯;它也會將 WindowsControlLibrary1 複製到 `MFC03` 專案目錄中，以便程式執行。

1. 在現有的 `#include` 語句結尾處，將 `#include <afxwinforms.h>` 新增至*pch* （Visual Studio 2017 和更早版本中的*stdafx.h* ）。

1. 加入子類別 `CDialog`的新類別。

   以滑鼠右鍵按一下專案名稱，並加入子類別 `CDialog`的 MFC 類別（稱為 CHostForWinForm）。 由於您不需要對話方塊資源，您可以刪除資源識別碼（選取 [**資源檢視**]，展開對話方塊資料夾，然後刪除 [`IDD_HOSTFORWINFORM` 資源 **]** 。  然後，在程式碼中移除對識別碼的任何參考）。

1. 以 `CWinFormsDialog<WindowsControlLibrary1::UserControl1>`取代 CHostForWinForm 中的 `CDialog` 和 CHostForWinForm .cpp 檔案。

1. 在 CHostForWinForm 類別上呼叫 DoModal。

   在 MFC03 中，新增 `#include "HostForWinForm.h"`。

   在 CMFC03App：： InitInstance 定義中的 return 語句之前，加入：

    ```cpp
    CHostForWinForm m_HostForWinForm;
    m_HostForWinForm.DoModal();
    ```

1. 建置並執行專案。

   在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。

   在 [**調試**] 功能表上，按一下 [**啟動但不進行調試**]。

   接下來，您將加入程式碼，以從 MFC 應用程式監視 Windows Forms 上控制項的狀態。

1. 新增 OnInitDialog 的處理常式。

   顯示 [**屬性**] 視窗（F4）。 在**類別檢視**中，選取 [CHostForWinForm]。 在 [**屬性**] 視窗中，選取 [覆寫]，並在 OnInitDialog 的資料列中按一下左側資料行，然後選取 [\< 新增 >]。 這會將下列這一行新增至 CHostForWinForm：

    ```cpp
    virtual BOOL OnInitDialog();
    ```

1. 定義 OnInitDialog （在 CHostForWinForm 中），如下所示：

    ```cpp
    BOOL CHostForWinForm::OnInitDialog() {
       CWinFormsDialog<WindowsControlLibrary1::UserControl1>::OnInitDialog();
       GetControl()->button1->Click += MAKE_DELEGATE(System::EventHandler, OnButton1);
       return TRUE;
    }
    ```

1. 接下來，新增 OnButton1 處理常式。 將下列幾行新增至 CHostForWinForm 中 CHostForWinForm 類別的 public 區段：

    ```cpp
    virtual void OnButton1( System::Object^ sender, System::EventArgs^ e );

    BEGIN_DELEGATE_MAP( CHostForWinForm )
       EVENT_DELEGATE_ENTRY( OnButton1, System::Object^, System::EventArgs^ );
    END_DELEGATE_MAP()
    ```

   在 CHostForWinForm 中，新增下列定義：

    ```cpp
    void CHostForWinForm::OnButton1( System::Object^ sender, System::EventArgs^ e )
    {
       System::Windows::Forms::MessageBox::Show("test");
    }
    ```

1. 建置並執行專案。 當您按一下 [Windows] 表單上的按鈕時，MFC 應用程式中的程式碼就會執行。

    接下來，您將新增程式碼，以便在 Windows Form 的文字方塊中，從 MFC 程式碼顯示值。

1. 在 CHostForWinForm 的 CHostForWinForm 類別的 public 區段中，新增下列宣告：

    ```cpp
    CString m_sEditBoxOnWinForm;
    ```

1. 在 CHostForWinForm 的 DoDataExchange 定義中，將下列三行新增至函式的結尾：

    ```cpp
    if (pDX->m_bSaveAndValidate)
       m_sEditBoxOnWinForm = CString( GetControl()->textBox1->Text);
    else
       GetControl()->textBox1->Text = gcnew System::String(m_sEditBoxOnWinForm);
    ```

1. 在 CHostForWinForm 的 OnButton1 定義中，將下列三行新增至函式的結尾：

    ```cpp
    this->UpdateData(TRUE);
    System::String ^ z = gcnew System::String(m_sEditBoxOnWinForm);
    System::Windows::Forms::MessageBox::Show(z);
    ```

1. 建置並執行專案。

## <a name="see-also"></a>請參閱

[在 MFC 中使用 Windows Form 使用者控制項](../dotnet/using-a-windows-form-user-control-in-mfc.md)<xref:System.Windows.Forms.UserControl?displayProperty=fullName>

