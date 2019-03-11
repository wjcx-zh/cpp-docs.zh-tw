---
title: 將 Windows Form 使用者控制項裝載為 MFC 檢視
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms controls [C++], hosting as an MFC view
- hosting Windows Forms control [C++]
ms.assetid: 43c02ab4-1366-434c-a980-0b19326d6ea0
ms.openlocfilehash: 9c59f28739ab94210c16bd800a48997f3f2282df
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57739793"
---
# <a name="hosting-a-windows-forms-user-control-as-an-mfc-view"></a>將 Windows Form 使用者控制項裝載為 MFC 檢視

MFC 會使用 CWinFormsView 類別來裝載 Windows Forms 使用者控制項的 MFC 檢視中。 MFC Windows Form 檢視是 ActiveX 控制項。 使用者控制項裝載為原生檢視的子系，而且佔用的原生檢視整個工作區。

最後的結果類似於所使用的模型[CFormView 類別](../mfc/reference/cformview-class.md)。 這可讓您充分利用 Windows Form 設計工具和執行階段，來建立豐富的以 form 為基礎的檢視。

MFC Windows Form 檢視是 ActiveX 控制項，因為它們並沒有相同`hwnd`為 MFC 檢視。 不能將它們傳遞為指標的也[CView](../mfc/reference/cview-class.md)檢視。 一般情況下，若要使用 Windows Form 檢視，並較不 Win32 依賴使用.NET Framework 方法。

顯示 Windows Form 搭配 MFC 使用的範例應用程式，請參閱[MFC 與 Windows Form 整合](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en)。

## <a name="in-this-section"></a>本節內容

[如何：建立使用者控制項並裝載 MDI 檢視](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)

[如何：新增命令傳送至 Windows Forms 控制項](../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)

[如何：呼叫 Windows Forms 控制項的屬性和方法](../dotnet/how-to-call-properties-and-methods-of-the-windows-forms-control.md)

## <a name="see-also"></a>另請參閱

[在 MFC 中使用 Windows Forms 使用者控制項](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
[如何：撰寫複合控制項](/dotnet/framework/winforms/controls/how-to-author-composite-controls)
