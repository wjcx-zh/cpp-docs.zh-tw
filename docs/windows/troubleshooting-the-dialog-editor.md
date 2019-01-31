---
title: 疑難排解 對話方塊編輯器 （c + +）
ms.date: 11/04/2016
helpviewer_keywords:
- controls [C++], troubleshooting
- Dialog Editor [C++], troubleshooting
- dialog boxes [C++], troubleshooting
- InitCommonControls
- RichEdit 1.0 control
- rich edit controls [C++], RichEdit 1.0
ms.assetid: 21882868-5ac4-4a41-a4a6-eaaa059402ea
ms.openlocfilehash: fe0fe704b5c17d0db4e3419f29d21f0e60bc4211
ms.sourcegitcommit: 5270117dbecc4c49bca0cf10b927bae3c9930038
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/31/2019
ms.locfileid: "55484951"
---
# <a name="troubleshooting-the-dialog-editor-c"></a>疑難排解 對話方塊編輯器 （c + +）

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

以下是一些您應該要注意在 c + + 中工作時的問題** 對話方塊**編輯器：

## <a name="adding-controls-to-a-dialog-causes-the-dialog-to-no-longer-function"></a>將控制項加入至對話方塊會造成對話方塊無法再運作

通用控制項或 rich edit 控制項加入對話方塊中之後, 則不會顯示當您測試對話方塊中，或對話方塊本身就不會出現。

### <a name="example-of-the-problem"></a>問題範例

1. 建立 Win32 專案中，修改應用程式設定，讓您建立 Windows 應用程式 （而不將主控台應用程式）。

1. 在 [資源檢視](../windows/resource-view-window.md)，按兩下.rc 檔案。

1. 在 對話方塊 選項中，按兩下**關於** 方塊中。

1. 新增**IP 位址控制項**對話方塊中。

1. 儲存並**重建所有**。

1. 執行此程式。

1. 在對話方塊中的**幫助** 功能表中，按一下**有關**命令; 沒有對話方塊會顯示。

### <a name="the-cause"></a>原因

目前， ** 對話方塊**編輯器不會自動將程式碼加入您的專案或您拖放的下列通用控制項 rich edit 控制項的對話方塊時。 也沒有 Visual Studio 提供錯誤或警告時就會發生此問題。 若要修正，以手動方式加入控制項的程式碼。

||||
|-|-|-|
|滑桿控制項|樹狀目錄控制項|日期時間選擇器|
|微調控制項|索引標籤控制項|月份的行事曆|
|進度控制項|動畫控制項|IP 位址控制項|
|熱鍵|Rich Edit 控制項|擴充的下拉式方塊|
|清單控制項|Rich Edit 2.0 控制項|自訂控制項|

### <a name="fix-for-common-controls"></a>通用控制項的修正

若要使用通用控制項 對話方塊上的，您必須呼叫[InitCommonControlsEx](/windows/desktop/api/commctrl/nf-commctrl-initcommoncontrolsex)或`AFXInitCommonControls`建立對話方塊之前。

### <a name="fix-for-richedit-controls"></a>修正 RichEdit 控制項

您必須呼叫`LoadLibrary`rich edit 控制項的。 如需詳細資訊，請參閱 <<c0> [ 關於 Rich Edit 控制項](/windows/desktop/Controls/about-rich-edit-controls)Windows SDK 中並[Rich Edit 控制項的概觀](../mfc/overview-of-the-rich-edit-control.md)。

### <a name="requirements"></a>需求

Win32

## <a name="using-the-richedit-10-control-with-mfc"></a>將 RichEdit 1.0 控制項與 MFC 一起使用

若要使用 RichEdit 控制項，您必須先呼叫[AfxInitRichEdit2](../mfc/reference/application-information-and-management.md#afxinitrichedit2)載入 RichEdit 2.0 控制項 (RICHED20。DLL)，或呼叫[AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit)載入較舊的 RichEdit 1.0 控制項 (RICHED32。DLL)。

您可以使用目前[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)類別與較舊的 RichEdit 1.0 控制項，但`CRichEditCtrl`只設計來支援 RichEdit 2.0 控制項。 RichEdit 1.0 和 RichEdit 2.0 很類似，因為大部分的方法就會運作。 不過請注意有一些差異，因此有些方法可能會無法正確運作，或完全無法運作的 1.0 和 2.0 控制項之間。

### <a name="requirements"></a>需求

MFC

## <a name="see-also"></a>另請參閱

[對話方塊編輯器](../windows/dialog-editor.md)