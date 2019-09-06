---
title: 將 Windows Form 使用者控制項裝載至 MFC 對話方塊中
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- hosting Windows Forms control [C++]
- Windows Forms [C++], MFC support
ms.assetid: 9f66ee52-b7cb-4ffd-8306-392a5da990d8
ms.openlocfilehash: 22f2c5c6c162e459470f9babab66c61c096540ec
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/31/2019
ms.locfileid: "70311862"
---
# <a name="hosting-a-windows-form-user-control-in-an-mfc-dialog-box"></a>將 Windows Form 使用者控制項裝載至 MFC 對話方塊中

MFC 會將 Windows Forms 控制項裝載為特殊類型的 activex 控制項，並使用 activex 介面和<xref:System.Windows.Forms.Control>類別的屬性和方法與控制項進行通訊。 建議您使用 .NET Framework 的屬性和方法來操作控制項。

如需顯示與 MFC 搭配使用之 Windows Forms 的範例應用程式，請參閱[mfc 和 Windows Forms 整合](https://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en)。

> [!NOTE]
>  在目前的版本中， `CDialogBar`物件無法裝載 Windows Forms 控制項。

## <a name="in-this-section"></a>本節內容

[如何：建立使用者控制項並裝載至對話方塊中](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)

[如何：使用 Windows Forms 執行 DDX/DDV 資料系結](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)

[如何：從原生 C++ 類別接收 Windows Forms 事件](../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)

## <a name="reference"></a>參考資料

[CWinFormsControl 類別](../mfc/reference/cwinformscontrol-class.md)&#124; [CDialog 類別](../mfc/reference/cdialog-class.md) &#124; [CWnd 類別](../mfc/reference/cwnd-class.md) &#124;<xref:System.Windows.Forms.Control>

## <a name="see-also"></a>另請參閱

[在 MFC 中使用 Windows Forms 使用者控制項](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
[Windows Forms/MFC 程式設計的差異](../dotnet/windows-forms-mfc-programming-differences.md)<br/>
[將 Windows Form 使用者控制項裝載為 MFC 檢視](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[將 Windows Forms 使用者控制項裝載成 MFC 對話方塊](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)
