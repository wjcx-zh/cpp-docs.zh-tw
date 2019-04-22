---
title: 在 MFC 中使用 Windows Form 使用者控制項
ms.date: 1/08/2018
helpviewer_keywords:
- MFC [C++], Windows Forms support
- interoperability [C++], Windows Forms in MFC
- interoperability [C++], MFC
- interop [C++], Windows Forms in MFC
- interop [C++], MFC
- Windows Forms [C++], MFC support
ms.assetid: 63fb099b-1dff-469c-9e34-dab52e122fcd
ms.openlocfilehash: 38c5c37712b430b137934d441056e60f2c130f78
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58773095"
---
# <a name="using-a-windows-form-user-control-in-mfc"></a>在 MFC 中使用 Windows Form 使用者控制項

使用 MFC Windows Form 支援類別，您可以裝載 Windows Form 控制項在 MFC 應用程式內為 ActiveX 控制項，MFC 對話方塊或檢視內。 此外，Windows Form 表單可以裝載成 MFC 對話方塊。

下列各節說明如何：

- 裝載 Windows Form 控制項在 MFC 對話方塊中。

- Windows Form 使用者控制項裝載為 MFC 檢視。

- 裝載成 MFC 對話方塊的 Windows Form 表單。

> [!NOTE]
> MFC Windows Form 整合只適用於以動態方式連結 MFC 的專案 (專案所在`_AFXDLL`定義)。

> [!NOTE]
> 當您建置您的應用程式使用的 DLL （mfcmifc80.dll 的參考） 的 MFC Windows Form 介面的私用 （已修改） 複本時，它將無法安裝在 GAC 中，除非您使用您自己的廠商金鑰來取代 Microsoft 金鑰。 如需有關簽署的組件的詳細資訊，請參閱[組件使用程式設計](/dotnet/framework/app-domains/programming-with-assemblies)並[強式名稱組件 （組件簽署） (C++/CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)。

如果您的 MFC 應用程式使用 Windows Forms，您需要重新發佈您的應用程式 mfcmifc80.dll 的參考。 如需詳細資訊，請參閱 <<c0> [ 轉散發 MFC 程式庫](../windows/redistributing-the-mfc-library.md)。

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

[使用者介面項目](../mfc/user-interface-elements-mfc.md)<br/>
[表單檢視](../mfc/form-views-mfc.md)
