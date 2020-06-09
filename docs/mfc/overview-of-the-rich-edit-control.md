---
title: Rich Edit 控制項的概觀
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC]
ms.assetid: ad589b9f-a3fd-4820-bf1f-6b1965997e68
ms.openlocfilehash: b99a5c6faaae4679b6aef67f240febbfb0f596e8
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617716"
---
# <a name="overview-of-the-rich-edit-control"></a>Rich Edit 控制項的概觀

> [!IMPORTANT]
> 如果您在對話方塊中使用 rich edit 控制項（不論您的應用程式是 SDI、MDI 還是以對話方塊為基礎），您必須在對話方塊顯示之前呼叫[AfxInitRichEdit](reference/application-information-and-management.md#afxinitrichedit)一次。 呼叫這個函式的一般位置是在程式的 `InitInstance` 成員函式中。 只需在第一次顯示對話方塊時呼叫它一次。 如果您使用 `AfxInitRichEdit`，不需要呼叫 `CRichEditView`。

Rich edit 控制項（[CRichEditCtrl](reference/cricheditctrl-class.md)）提供用於格式化文字的程式設計介面。 然而，應用程式必須實作所有必要的使用者介面元件，讓使用者能夠執行格式化作業。 也就是說，Rich Edit 控制項支援變更所選取文字中的字元或段落屬性。 字元屬性的範例為粗體、斜體、字型系列和字型的點數大小。 段落屬性的範例包括對齊、邊界和定位停駐點。 不過，使用者介面全由您決定提供，不論是工具列按鈕、功能表項目或格式字元對話方塊。 也有函式可查詢 Rich Edit 控制項，以顯示目前選取範圍的屬性。 請使用這些函式顯示屬性的目前設定，例如，如果選取範圍有粗體字元格式屬性，則在命令 UI 中設定核取記號。

如需有關字元和段落格式的詳細資訊，請參閱本主題稍後的[字元格式設定](character-formatting-in-rich-edit-controls.md)和[段落格式](paragraph-formatting-in-rich-edit-controls.md)。

Rich Edit 控制項支援用於多行編輯控制項的大部分作業和通知訊息。 因此，已使用編輯控制項的應用程式可以輕鬆地變更成使用 Rich Edit 控制項。 其他訊息和通知讓應用程式能夠存取 Rich Edit 控制項的獨特功能。 如需編輯控制項的詳細資訊，請參閱[CEdit](reference/cedit-class.md)。

如需通知的詳細資訊，請參閱本主題稍後[的來自 Rich Edit 控制項的通知](notifications-from-a-rich-edit-control.md)。

## <a name="see-also"></a>另請參閱

[使用 CRichEditCtrl](using-cricheditctrl.md)<br/>
[控制項](controls-mfc.md)
