---
title: 將 Windows Form 使用者控制項裝載成 MFC 對話方塊
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms [C++], hosting as MFC Dialog
- hosting Windows Forms control [C++]
ms.assetid: 0434a9d7-8b14-48e6-ad69-9ba9a684677a
ms.openlocfilehash: 44123e3cbad3115dc990cd8dc9f1316994560656
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580917"
---
# <a name="hosting-a-windows-form-user-control-as-an-mfc-dialog-box"></a>將 Windows Form 使用者控制項裝載成 MFC 對話方塊

MFC 提供樣板類別[CWinFormsDialog](../mfc/reference/cwinformsdialog-class.md) ，讓您可以裝載的 Windows Forms 使用者控制項 (<xref:System.Windows.Forms.UserControl>) 在強制回應或非強制回應的 MFC 對話方塊中。 `CWinFormsDialog` 衍生自 MFC 類別[CDialog](../mfc/reference/cdialog-class.md)，因此可以啟動 [] 對話方塊中，為強制回應或非強制回應。

此程序，`CWinFormsDialog`用來將使用者控制項裝載是類似於中所述[MFC 對話方塊中的 Windows Forms 使用者控制項裝載](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)。 不過，`CWinFormsDialog`管理的初始化和裝載使用者控制項，使它不需要以手動方式程式設計。

顯示 Windows Form 搭配 MFC 使用的範例應用程式，請參閱[MFC 與 Windows Form 整合](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en)。

### <a name="to-create-the-mfc-host-application"></a>若要建立 MFC 主應用程式

1. 建立 MFC 應用程式專案。

   在上**檔案**功能表上，選取**新增**，然後按一下**專案**。 在  **Visual c + +** 資料夾中，選取**MFC 應用程式**。

   在 **名稱**方塊中，輸入`MFC03`並將方案設定變更為**加入至方案**。按一下 **確定**。

   在  **MFC 應用程式精靈**，接受所有預設值，然後按一下 **完成**。 這會建立多個的文件介面的 MFC 應用程式。

1. 設定專案。

   在 **方案總管**，以滑鼠右鍵按一下**MFC03**專案節點，然後選擇**屬性**。 **屬性頁** 對話方塊隨即出現。

   在 **屬性頁**對話方塊中，於**組態屬性**樹狀結構控制項中選取**一般**，然後在**專案預設值**區段中，將**Common Language Runtime 支援**要**Common Language Runtime 支援 (/ clr)**。 按一下 [確定 **Deploying Office Solutions**]。

1. 新增.NET 控制項的參考。

   在 [**方案總管] 中**，以滑鼠右鍵按一下**MFC03**專案節點，然後選擇**新增**，**參考**。 在**屬性頁**，按一下**加入新參考**，選取 windowscontrollibrary1 (下**專案** 索引標籤)，然後按一下**確定**。 這會將參考新增的形式[/FU](../build/reference/fu-name-forced-hash-using-file.md)編譯器選項，如此將會編譯程式; 它也會將 windowscontrollibrary1.dll 複製到`MFC03`專案目錄，以便執行程式。

1. 新增`#include <afxwinforms.h>`至 stdafx.h 中結尾的現有`#include`陳述式。

1. 加入新的類別子類別化`CDialog`。

   以滑鼠右鍵按一下專案名稱，並新增 MFC 類別 (稱為 CHostForWinForm) 子類別化`CDialog`。 因為您不需要此對話方塊資源，您可以刪除的資源識別碼 (選取**資源檢視**，展開**對話方塊**資料夾，然後刪除`IDD_HOSTFORWINFORM`資源。  然後，移除任何參照的識別碼在程式碼中。）。

1. 取代`CDialog`CHostForWinForm.h 和 CHostForWinForm.cpp 檔案中`CWinFormsDialog<WindowsControlLibrary1::UserControl1>`。

1. 呼叫 CHostForWinForm 類別上的 DoModal。

   在 mfc03.cpp 中，新增`#include "HostForWinForm.h"`。

   之前在 CMFC03App::InitInstance 定義中的 return 陳述式，加入：

    ```cpp
    CHostForWinForm m_HostForWinForm;
    m_HostForWinForm.DoModal();
    ```

1. 建置並執行專案。

   在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。

   在 **偵錯**功能表上，按一下**啟動但不偵錯**。

   接下來，您將加入程式碼來監視在 MFC 應用程式從 Windows Forms 上控制項的狀態。

9. 加入 oninitdialog 的處理常式。

   顯示**屬性**視窗 (F4)。 在 **類別檢視**，選取 CHostForWinForm。 在 [**屬性**] 視窗中，選取覆寫在 OnInitDialog 的資料列，按一下左邊的資料行，並選取\<新增 >。 這會將下面這一行加入到 chostforwinform.h 中：

    ```cpp
    virtual BOOL OnInitDialog();
    ```

10. 定義 OnInitDialog （在 CHostForWinForm.cpp 中) 如下所示：

    ```
    BOOL CHostForWinForm::OnInitDialog() {
       CWinFormsDialog<WindowsControlLibrary1::UserControl1>::OnInitDialog();
       GetControl()->button1->Click += MAKE_DELEGATE(System::EventHandler, OnButton1);
       return TRUE;
    }
    ```

11. 接下來，加入 OnButton1 處理常式。 將下列幾行新增到 CHostForWinForm.h 中 CHostForWinForm 類別的 public 區段：

    ```
    virtual void OnButton1( System::Object^ sender, System::EventArgs^ e );

    BEGIN_DELEGATE_MAP( CHostForWinForm )
       EVENT_DELEGATE_ENTRY( OnButton1, System::Object^, System::EventArgs^ );
    END_DELEGATE_MAP()
    ```

   在 CHostForWinForm.cpp 中加入下列定義：

    ```
    void CHostForWinForm::OnButton1( System::Object^ sender, System::EventArgs^ e )
    {
       System::Windows::Forms::MessageBox::Show("test");
    }
    ```

12. 建置並執行專案。 當您按一下按鈕，也就是 Windows Form 上，則會執行 MFC 應用程式中的程式碼。

   接下來您將加入從 MFC 程式碼將值顯示在文字方塊中，Windows Form 上的程式碼。

13. 在 CHostForWinForm.h 中 CHostForWinForm 類別的 public 區段，新增下列宣告：

    ```
    CString m_sEditBoxOnWinForm;
    ```

14. 在 chostforwinform.cpp 的 DoDataExchange 定義中，加入函式結尾中的下列三行：

    ```
    if (pDX->m_bSaveAndValidate)
       m_sEditBoxOnWinForm = CString( GetControl()->textBox1->Text);
    else
       GetControl()->textBox1->Text = gcnew System::String(m_sEditBoxOnWinForm);
    ```

15. 在 chostforwinform.cpp 的 OnButton1 定義中，加入函式結尾中的下列三行：

    ```
    this->UpdateData(TRUE);
    System::String ^ z = gcnew System::String(m_sEditBoxOnWinForm);
    System::Windows::Forms::MessageBox::Show(z);
    ```

16. 建置並執行專案。

## <a name="see-also"></a>另請參閱

<xref:System.Windows.Forms.UserControl?displayProperty=fullName>
[在 MFC 中使用 Windows Form 使用者控制項](../dotnet/using-a-windows-form-user-control-in-mfc.md)