---
title: Rich Edit 控制項的概觀
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC]
ms.assetid: ad589b9f-a3fd-4820-bf1f-6b1965997e68
ms.openlocfilehash: 9ef696bc348dfb18b797b487224b97261020e11c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366877"
---
# <a name="overview-of-the-rich-edit-control"></a>Rich Edit 控制項的概觀

> [!IMPORTANT]
> 如果在對話框中使用豐富的編輯控件(無論您的應用程式是 SDI、MDI 還是基於對話方塊),則必須在顯示對話框之前調用[AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit)一次。 呼叫這個函式的一般位置是在程式的 `InitInstance` 成員函式中。 只需在第一次顯示對話方塊時呼叫它一次。 如果您使用 `AfxInitRichEdit`，不需要呼叫 `CRichEditView`。

豐富的編輯控制檔([CRichEditCtrl)](../mfc/reference/cricheditctrl-class.md)為文字格式設定提供編程介面. 然而，應用程式必須實作所有必要的使用者介面元件，讓使用者能夠執行格式化作業。 也就是說，Rich Edit 控制項支援變更所選取文字中的字元或段落屬性。 字元屬性的範例為粗體、斜體、字型系列和字型的點數大小。 段落屬性的範例包括對齊、邊界和定位停駐點。 不過，使用者介面全由您決定提供，不論是工具列按鈕、功能表項目或格式字元對話方塊。 也有函式可查詢 Rich Edit 控制項，以顯示目前選取範圍的屬性。 請使用這些函式顯示屬性的目前設定，例如，如果選取範圍有粗體字元格式屬性，則在命令 UI 中設定核取記號。

關於字元與段落格式的詳細資訊,請參考主旨後面的[字元格式](../mfc/character-formatting-in-rich-edit-controls.md)與[段落格式](../mfc/paragraph-formatting-in-rich-edit-controls.md)。

Rich Edit 控制項支援用於多行編輯控制項的大部分作業和通知訊息。 因此，已使用編輯控制項的應用程式可以輕鬆地變更成使用 Rich Edit 控制項。 其他訊息和通知讓應用程式能夠存取 Rich Edit 控制項的獨特功能。 有關編輯控制項資訊,請參閱[CEdit](../mfc/reference/cedit-class.md)。

有關通知的詳細資訊,請參閱本主題後面的[「豐富編輯控件通知](../mfc/notifications-from-a-rich-edit-control.md)」。

## <a name="see-also"></a>另請參閱

[使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
