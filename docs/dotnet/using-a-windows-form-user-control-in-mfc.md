---
title: 在 MFC 中使用 Windows Form 使用者控制項
ms.date: 01/08/2018
helpviewer_keywords:
- MFC [C++], Windows Forms support
- interoperability [C++], Windows Forms in MFC
- interoperability [C++], MFC
- interop [C++], Windows Forms in MFC
- interop [C++], MFC
- Windows Forms [C++], MFC support
ms.assetid: 63fb099b-1dff-469c-9e34-dab52e122fcd
ms.openlocfilehash: efabbf84778d925ec1de03f5f4ea0ca09185bd81
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926059"
---
# <a name="using-a-windows-form-user-control-in-mfc"></a>在 MFC 中使用 Windows Form 使用者控制項

使用 MFC Windows Forms 支援類別，您可以將 MFC 應用程式內的 Windows Forms 控制項裝載為 MFC 對話方塊或視圖中的 ActiveX 控制項。 此外，Windows Forms 表單也可以裝載為 MFC 對話方塊。

下列各節說明如何：

- 在 MFC 對話方塊中裝載 Windows Forms 控制項。

- 將 Windows Forms 的使用者控制項裝載為 MFC 視圖。

- 將 Windows Forms 表單裝載為 MFC 對話方塊。

> [!NOTE]
> Mfc Windows Forms 整合只適用于以 mfc （定義的專案`_AFXDLL` ）動態連結的專案。

> [!NOTE]
> 當您使用 MFC Windows Forms 介面 DLL （mfcmifc80）的私用（已修改）複本來建立應用程式時，除非您使用自己的廠商金鑰來取代 Microsoft 金鑰，否則它將無法安裝在 GAC 中。 如需元件簽署的詳細資訊，請參閱[使用元件](/dotnet/framework/app-domains/programming-with-assemblies)進行程式設計和[強式名稱元件（C++元件簽署）（/cli）](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)。

如果您的 MFC 應用程式使用 Windows Forms，您需要使用您的應用程式轉散發 mfcmifc80。 如需詳細資訊，請參閱轉散發[MFC 程式庫](../windows/redistributing-the-mfc-library.md)。

## <a name="in-this-section"></a>本節內容

[將 Windows Forms 使用者控制項裝載至 MFC 對話方塊中](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)

[將 Windows Form 使用者控制項裝載為 MFC 檢視](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)

[將 Windows Forms 使用者控制項裝載成 MFC 對話方塊](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)

## <a name="reference"></a>參考資料

[CWinFormsControl 類別](../mfc/reference/cwinformscontrol-class.md)

[CWinFormsDialog 類別](../mfc/reference/cwinformsdialog-class.md)

[CWinFormsView 類別](../mfc/reference/cwinformsview-class.md)

[ICommandSource 介面](../mfc/reference/icommandsource-interface.md)

[ICommandTarget 介面](../mfc/reference/icommandtarget-interface.md)

[ICommandUI 介面](../mfc/reference/icommandui-interface.md)

[IView 介面](../mfc/reference/iview-interface.md)

[CommandHandler](../atl/commandhandler.md)

[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)

[UICheckState](../mfc/reference/uicheckstate-enumeration.md)

## <a name="related-sections"></a>相關章節

[Windows Forms](/dotnet/framework/winforms/index)

[Windows Forms 控制項](/dotnet/framework/winforms/controls/index)

## <a name="see-also"></a>另請參閱

[使用者介面元素](../mfc/user-interface-elements-mfc.md)<br/>
[表單檢視](../mfc/form-views-mfc.md)
