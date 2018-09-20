---
title: 如何： 執行 DDX-DDV 資料繫結 Windows form |Microsoft Docs
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], hosting a Windows Forms Control
- Windows Forms [C++], MFC support
ms.assetid: b2957370-cf1f-4779-94ac-228cd393686c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 87e6eb6e845a7e900568494ed2834f23b9f6c175
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418045"
---
# <a name="how-to-do-ddxddv-data-binding-with-windows-forms"></a>如何：使用 Windows Form 執行 DDX/DDV 資料繫結

[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)呼叫[CWinFormsControl::CreateManagedControl](../mfc/reference/cwinformscontrol-class.md#createmanagedcontrol)建立控制項，比對資源的控制項 id。 如果您使用`DDX_ManagedControl`for`CWinFormsControl`控制項 （在精靈產生的程式碼），您不應該呼叫`CreateManagedControl`明確針對相同的控制項。

呼叫`DDX_ManagedControl`中[CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)建立控制項從 資源識別碼。 資料交換，您不需要使用 Windows Form 控制項使用 DDX/DDV 函式。 相反地，您可以在其中放置程式碼，以存取受管理之控制項的屬性`DoDataExchange`對話方塊 （或檢視表） 類別，如下列範例所示的方法。

下列範例示範如何將原生的 c + + 字串繫結至.NET 使用者控制項。

## <a name="example"></a>範例

以下是範例 MFC 字串的 DDX/DDV 資料繫結`m_str`使用者定義`NameText`.NET 使用者控制項的屬性。

控制項時，會建立[CDialog::OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)呼叫`CMyDlg::DoDataExchange`第一次，因此任何程式碼，會參考`m_UserControl`必須緊跟在後`DDX_ManagedControl`呼叫。

您可以在您建立的 MFC01 應用程式中實作此程式碼[如何： 在對話方塊中建立使用者控制項並裝載](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)。

下列程式碼置於 CMFC01Dlg 的宣告：

```
class CMFC01Dlg : public CDialog
{
   CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_MyControl;
   CString m_str;
};
```

## <a name="example"></a>範例

下列程式碼置於 CMFC01Dlg 的實作：

```
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

現在我們會新增處理常式方法，按一下 [確定] 按鈕。 按一下 [**資源檢視**] 索引標籤。在 [資源] 檢視中，按兩下`IDD_MFC01_DIALOG`。 對話方塊資源隨即出現在 資源編輯器。 然後按兩下 [確定] 按鈕...

會定義處理常式，如下所示。

```
void CMFC01Dlg::OnBnClickedOk()
{
   AfxMessageBox(CString(m_MyControl.GetControl()->textBox1->Text));
   OnOK();
}
```

## <a name="example"></a>範例

並將下列這一行新增至 BOOL CMFC01Dlg::OnInitDialog() 的實作。

```
m_MyControl.GetControl()->textBox1->Text = "hello";
```

您現在可以建置並執行應用程式。 請注意，在文字方塊中的任何文字將會顯示在快顯訊息方塊應用程式關閉時。

## <a name="see-also"></a>另請參閱

[CWinFormsControl 類別](../mfc/reference/cwinformscontrol-class.md)<br/>
[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)<br/>
[CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)