---
title: 將 Windows Form 使用者控制項裝載為 MFC 檢視
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms controls [C++], hosting as an MFC view
- hosting Windows Forms control [C++]
ms.assetid: 43c02ab4-1366-434c-a980-0b19326d6ea0
ms.openlocfilehash: 9eb157ecbc738e1d7a1c3022d5f156fb590e8f04
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2019
ms.locfileid: "73704121"
---
# <a name="hosting-a-windows-forms-user-control-as-an-mfc-view"></a>將 Windows Form 使用者控制項裝載為 MFC 檢視

MFC 會使用 CWinFormsView 類別，在 MFC 視圖中裝載 Windows Forms 的使用者控制項。 MFC Windows Forms views 是 ActiveX 控制項。 使用者控制項會裝載為原生視圖的子系，並佔用原生視圖的整個工作區。

最後的結果會與[CFormView 類別](../mfc/reference/cformview-class.md)所使用的模型類似。 這可讓您利用 Windows Forms 的設計工具和執行時間來建立以表單為基礎的豐富視圖。

因為 MFC Windows Forms views 是 ActiveX 控制項，所以沒有與 MFC views 相同的 `hwnd`。 此外，它們也無法當做[CView](../mfc/reference/cview-class.md)視圖的指標來傳遞。 一般來說，請使用 .NET Framework 方法來處理 Windows Forms 的 views，並在 Win32 上依賴較少的。

如需顯示與 MFC 搭配使用之 Windows Forms 的範例應用程式，請參閱[mfc 和 Windows Forms 整合](https://www.microsoft.com/en-us/download/details.aspx?id=2113)。

## <a name="in-this-section"></a>本章節內容

[如何：建立使用者控制項並裝載 MDI 檢視](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)

[如何：新增命令傳送至 Windows Forms 控制項](../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)

[如何：呼叫 Windows Forms 控制項的屬性和方法](../dotnet/how-to-call-properties-and-methods-of-the-windows-forms-control.md)

## <a name="see-also"></a>請參閱

[在 MFC 中使用 Windows Forms 使用者控制項](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
[操作說明：撰寫複合控制項](/dotnet/framework/winforms/controls/how-to-author-composite-controls)
