---
title: 將 Windows Form 使用者控制項裝載至 MFC 對話方塊中
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- hosting Windows Forms control [C++]
- Windows Forms [C++], MFC support
ms.assetid: 9f66ee52-b7cb-4ffd-8306-392a5da990d8
ms.openlocfilehash: 2704e04df3792edfee6c39f597fcbe71b6ce51b4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374490"
---
# <a name="hosting-a-windows-form-user-control-in-an-mfc-dialog-box"></a>將 Windows Form 使用者控制項裝載至 MFC 對話方塊中

MFC 將 Windows 窗體控制項模組託管為一種特殊的 ActiveX 控制項,並使用<xref:System.Windows.Forms.Control>ActiveX 介面以及 類的屬性和方法與控制元件通訊。 我們建議您使用 .NET Framework 屬性和方法對控制項進行操作。

有關顯示與 MFC 一起使用的 Windows 窗體的範例應用程式,請參考[MFC 與 Windows 元件整合](https://www.microsoft.com/download/details.aspx?id=2113)。

> [!NOTE]
> 在目前的版本中,`CDialogBar`物件無法承載 Windows 窗體控制件。

## <a name="in-this-section"></a>本節內容

[如何：建立使用者控制項並裝載至對話方塊中](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)

[如何：使用 Windows Form 執行 DDX/DDV 資料繫結](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)

[如何：從原生 C++ 類別接收 Windows Form 事件](../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)

## <a name="reference"></a>參考

[CWinForms 控制類](../mfc/reference/cwinformscontrol-class.md)&#124; [CDialog 類](../mfc/reference/cdialog-class.md)&#124; [Cwnd 類](../mfc/reference/cwnd-class.md)&#124;<xref:System.Windows.Forms.Control>

## <a name="see-also"></a>另請參閱

[在 MFC 中使用 Windows Forms 使用者控制項](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
[視窗表單/MFC 程式設計差異](../dotnet/windows-forms-mfc-programming-differences.md)<br/>
[將 Windows Form 使用者控制項裝載為 MFC 檢視](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[將 Windows Form 使用者控制項裝載成 MFC 對話方塊](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)
