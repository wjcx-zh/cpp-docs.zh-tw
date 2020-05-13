---
title: 操作方式:使用 Windows 表單進行 DDX-DDV 資料繫結
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], hosting a Windows Forms Control
- Windows Forms [C++], MFC support
ms.assetid: b2957370-cf1f-4779-94ac-228cd393686c
ms.openlocfilehash: 31629a4db2559112ba49f5c069b08de7abdfc2db
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754357"
---
# <a name="how-to-do-ddxddv-data-binding-with-windows-forms"></a>如何：使用 Windows Form 執行 DDX/DDV 資料繫結

[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)呼叫[CWinForms 控制::建立託管控制](../mfc/reference/cwinformscontrol-class.md#createmanagedcontrol)以建立與資源控制 ID 符合的控制項。 如果用於`DDX_ManagedControl`控制項(在`CWinFormsControl`精靈生成的代碼中),則不應顯式調用`CreateManagedControl`同一控制件。

在`DDX_ManagedControl` [CWnd::DoDataExchange 中](../mfc/reference/cwnd-class.md#dodataexchange)調用,從資源 ID 創建控制項。 對於資料交換,您無需將 DDX/DDV 函數與 Windows 窗體控制項一起使用。 相反,您可以將代碼放在對話方塊(或視圖)`DoDataExchange`類的方法中訪問托管控件的屬性,如以下示例所示。

下面的範例展示如何將本機C++字串綁定到.NET 使用者控制項。

## <a name="example"></a>範例

下面是 MFC 字串的 DDX/DDV 資料綁定的`m_str`範例, 該字串具有 .NET 使用者`NameText`控制項的使用者定義 屬性。

當[CDialog::OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)首次`CMyDlg::DoDataExchange`調用 時創建該控制項`m_UserControl`,因此引用的任何代碼`DDX_ManagedControl`都必須在調用後出現。

您可以在「[如何:在對話框中創建使用者控制和主機」](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)中建立的 MFC01 應用程式中實現此代碼。

在 CMFC01Dlg 的聲明中放入以下代碼:

```
class CMFC01Dlg : public CDialog
{
   CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_MyControl;
   CString m_str;
};
```

## <a name="example"></a>範例

在 CMFC01Dlg 的實現中放入以下代碼:

```cpp
void CMFC01Dlg::DoDataExchange(CDataExchange* pDX)
{
   CDialog::DoDataExchange(pDX);
   DDX_ManagedControl(pDX, IDC_CTRL1, m_MyControl);

   if (pDX->m_bSaveAndValidate) {
      m_str = m_MyControl->textBox1->Text;
   } else
   {
      m_MyControl->textBox1->Text = gcnew System::String(m_str);
   }
}
```

## <a name="example"></a>範例

現在,我們將添加處理程式方法,按一下"確定"按鈕。 按下「**資源檢視」** 選項卡。在「資源檢視」中,按兩`IDD_MFC01_DIALOG`下 。 對話框資源將顯示在資源編輯器中。 然後按兩下「確定」 按鈕。

定義處理程式,如下所示。

```cpp
void CMFC01Dlg::OnBnClickedOk()
{
   AfxMessageBox(CString(m_MyControl.GetControl()->textBox1->Text));
   OnOK();
}
```

## <a name="example"></a>範例

並添加以下行的BOOL CMFC01Dlg實現::onInitDialog()。

```
m_MyControl.GetControl()->textBox1->Text = "hello";
```

您現在可以建置並執行應用程式。 請注意,當應用程式關閉時,文本框中的任何文本都將顯示在彈出消息框中。

## <a name="see-also"></a>另請參閱

[CWinFormsControl 類別](../mfc/reference/cwinformscontrol-class.md)<br/>
[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)<br/>
[CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)
