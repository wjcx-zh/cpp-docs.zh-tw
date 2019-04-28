---
title: 將 Windows Form 使用者控制項裝載至 MFC 對話方塊中
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- hosting Windows Forms control [C++]
- Windows Forms [C++], MFC support
ms.assetid: 9f66ee52-b7cb-4ffd-8306-392a5da990d8
ms.openlocfilehash: 56cf00da71fe6c47e39de2a8fc06df572a301a61
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222984"
---
# <a name="hosting-a-windows-form-user-control-in-an-mfc-dialog-box"></a>將 Windows Form 使用者控制項裝載至 MFC 對話方塊中

MFC ActiveX 控制項是特殊類型裝載的 Windows Form 控制項和使用 ActiveX 介面，以及屬性和方法的控制項與通訊<xref:System.Windows.Forms.Control>類別。 我們建議您使用.NET Framework 屬性和方法來操作控制項。

顯示 Windows Form 搭配 MFC 使用的範例應用程式，請參閱[MFC 與 Windows Form 整合](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en)。

> [!NOTE]
>  在目前的版本中，`CDialogBar`物件不能在裝載 Windows Form 控制項。

## <a name="in-this-section"></a>本節內容

[如何：建立使用者控制項並裝載至對話方塊中](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)

[如何：執行 DDX/DDV 資料繫結搭配 Windows Form](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)

[如何：從原生 C++ 類別接收 Windows Forms 事件](../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)

## <a name="reference"></a>參考資料

[CWinFormsControl Class](../mfc/reference/cwinformscontrol-class.md) &#124; [CDialog Class](../mfc/reference/cdialog-class.md) &#124; [CWnd Class](../mfc/reference/cwnd-class.md) &#124; <xref:System.Windows.Forms.Control>

## <a name="see-also"></a>另請參閱

[在 MFC 中使用 Windows Forms 使用者控制項](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
[Windows Forms/MFC 程式設計的差異](../dotnet/windows-forms-mfc-programming-differences.md)<br/>
[將 Windows Form 使用者控制項裝載為 MFC 檢視](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[將 Windows Forms 使用者控制項裝載成 MFC 對話方塊](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)
