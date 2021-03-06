---
title: HOW TO：呼叫控制項屬性和方法的 Windows Form
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- method calls, Windows Forms
- calling methods, Windows Forms control
- calling properties, Windows Forms control
- Windows Forms controls [C++], methods
- calling properties
- Windows Forms controls [C++], properties
ms.assetid: 6e647d8a-fdaa-4aa1-b3fe-04f15cff8eb3
ms.openlocfilehash: 61b565839b3f3c24670819fdcf2dde558e3461ac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152806"
---
# <a name="how-to-call-properties-and-methods-of-the-windows-forms-control"></a>HOW TO：呼叫控制項屬性和方法的 Windows Form

因為[CWinFormsView::GetControl](../mfc/reference/cwinformsview-class.md#getcontrol)傳回的指標<xref:System.Windows.Forms.Control?displayProperty=fullName>，並不是指標`WindowsControlLibrary1::UserControl1`，建議您新增的使用者控制項類型的成員，並將它在初始化[IView::OnInitialUpdate](../mfc/reference/iview-interface.md#oninitialupdate). 現在您可以呼叫方法和屬性使用`m_ViewControl`。

本主題假設您先前已完成[How to:在對話方塊中建立使用者控制項並裝載](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)和[How to:建立使用者控制項並裝載 MDI 檢視](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)。

### <a name="to-create-the-mfc-host-application"></a>若要建立 MFC 主應用程式

1. 開啟您建立的 MFC 應用程式[How to:建立使用者控制項並裝載 MDI 檢視](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)。

1. 將下行新增到公用的覆寫區段`CMFC02View`類別在 MFC02View.h 中的宣告。

   `gcroot<WindowsFormsControlLibrary1::UserControl1 ^> m_ViewControl;`

1. 新增 OnInitialupdate 覆寫。

   顯示**屬性**視窗 (F4)。 在 **類別檢視**(CTRL + SHIFT + C)，選取 CMFC02View 類別。 在 [**屬性**] 視窗中，選取用於覆寫的圖示。 往下到清單 OnInitialUpdate Scoll。 按一下下拉式清單並選取\<新增 >。 在 MFC02View.cpp。 請確定 OnInitialUpdate 函式的主體，如下所示：

    ```
    CWinFormsView::OnInitialUpdate();
    m_ViewControl = safe_cast<WindowsFormsControlLibrary1::UserControl1 ^>(this->GetControl());
    m_ViewControl->textBox1->Text = gcnew System::String("hi");
    ```

1. 建置並執行專案。

   在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。

   在 **偵錯**功能表上，按一下**啟動但不偵錯**。

   請注意，文字方塊現在已初始化。

## <a name="see-also"></a>另請參閱

[將 Windows Form 使用者控制項裝載為 MFC 檢視](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)
