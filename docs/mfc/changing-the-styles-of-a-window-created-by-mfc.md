---
title: 變更 MFC 所建立之視窗的樣式
ms.date: 11/04/2016
helpviewer_keywords:
- window styles [MFC]
- WS_OVERLAPPEDWINDOW macro [MFC]
- single document interface (SDI), changing window attributes
- MDI [MFC], window styles
- windows [MFC], MFC
- child windows [MFC], styles
- MFC, windows
- CFrameWnd class [MFC], window styles
- CREATESTRUCT macro [MFC]
- CMDIChildWnd class [MFC], changing window styles
- multidocument interface style
- PreCreateWindow method [MFC], window styles
- single document interface (SDI), style
- default window style
- defaults [MFC], window style
- PreCreateWindow method [MFC], changing window styles
- CMainFrame class [MFC]
- styles [MFC], windows
ms.assetid: 77fa4f03-96b4-4687-9ade-41e46f7e4b0a
ms.openlocfilehash: 221092eb25a4f044cda5b379d6774659d9e9d2d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374598"
---
# <a name="changing-the-styles-of-a-window-created-by-mfc"></a>變更 MFC 所建立之視窗的樣式

在其版本的函數中`WinMain`,MFC 為您註冊了幾個標準視窗類。 由於您通常不編輯 MFC`WinMain`的 ,因此該函數無法更改 MFC 默認視窗樣式。 本文介紹如何更改現有應用程式中此類預先註冊的視窗類的樣式。

## <a name="changing-styles-in-a-new-mfc-application"></a><a name="_core_changing_styles_in_a_new_mfc_application"></a>變更新的 MFC 應用程式中樣式

如果您使用的是 Visual C++ 2.0 或更高版本,則可以在創建應用程式時更改應用程式精靈中的預設視窗樣式。 在應用程式精靈的使用者介面功能頁中,您可以更改主框架視窗和 MDI 子視窗的樣式。 對於任一視窗類型,您可以指定其幀厚度(厚或薄)和以下任一:

- 視窗是否具有最小化控制項或最大化控制項。

- 視窗最初是否出現最小化、最大化,或者兩者均未出現。

對於主框架視窗,還可以指定視窗是否具有系統功能表。 對於 MDI 子視窗,可以指定視窗是否支援分割器窗格。

## <a name="changing-styles-in-an-existing-application"></a><a name="_core_changing_styles_in_an_existing_application"></a>變更現有應用程式中的樣式

如果要更改現有應用程式中的視窗屬性,請改用本文其餘部分中的說明。

要更改使用應用程式精靈建立的框架應用程式使用的預設視窗屬性,請覆蓋視窗的[PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow)虛擬成員函數。 `PreCreateWindow`允許應用程式訪問通常由[CDocTemplate](../mfc/reference/cdoctemplate-class.md)類在內部管理的創建過程。 框架在創建`PreCreateWindow`視窗之前調用。 通過修改傳遞給`PreCreateWindow`的[CREATETRUCT](/windows/win32/api/winuser/ns-winuser-createstructw)結構,應用程式可以更改用於創建視窗的屬性。 例如,為了確保視窗不使用標題,請使用以下位視操作:

[!code-cpp[NVC_MFCDocView#15](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_1.cpp)]

[CTRLBARS](../overview/visual-cpp-samples.md)範例應用程式演示了此用於更改視窗屬性的技術。 根據應用程式在中的`PreCreateWindow`更改,可能需要調用函數的基類實現。

以下討論包括SDI案與[MDI案](#_core_the_mdi_case)。

## <a name="the-sdi-case"></a><a name="_core_the_sdi_case"></a>SDI 案例

在單個文件介面 (SDI) 應用程式中,框架中的預設視窗樣式是**WS_OVERLAPPEDWINDOW**和**FWS_ADDTOTITLE**樣式的組合。 **FWS_ADDTOTITLE**是特定於 MFC 的樣式,用於指示框架將文檔標題添加到視窗的標題中。 要更改 SDI 應用程式中的視窗屬性,請重`PreCreateWindow`寫類 中`CFrameWnd`派生自的函數(應用程式`CMainFrame`精靈名稱 )。 例如：

[!code-cpp[NVC_MFCDocViewSDI#11](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_2.cpp)]

此代碼創建一個主框架視窗,沒有最小化和最大化按鈕,並且沒有相當大的邊框。 視窗最初居中在螢幕上。

## <a name="the-mdi-case"></a><a name="_core_the_mdi_case"></a>MDI 案例

在多個文件介面 (MDI) 應用程式中更改子視窗的視窗樣式還需要多做一些工作。 默認情況下,使用應用程式嚮導創建的 MDI 應用程式使用在 MFC 中定義的預設[CMDIChildwnd](../mfc/reference/cmdichildwnd-class.md)類。 要更改 MDI 子視窗的視窗樣式,`CMDIChildWnd`必須從專案中派生一個新類,`CMDIChildWnd`並將對 專案中的所有引用替換為對新類的引用。 最有可能的是,應用程式中的唯一引用`CMDIChildWnd`位於`InitInstance`應用程式的成員函數中。

MDI 應用程式中使用的預設視窗樣式是**WS_CHILD、WS_OVERLAPPEDWINDOW****和FWS_ADDTOTITLE**樣式的群組**WS_OVERLAPPEDWINDOW**。 要更改 MDI 應用程式子視窗的視窗屬性,請覆蓋派生`CMDIChildWnd`自 的 類中的[PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow)函數。 例如：

[!code-cpp[NVC_MFCDocView#16](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_3.cpp)]

此代碼創建沒有"最大化"按鈕的 MDI 子視窗。

### <a name="what-do-you-want-to-know-more-about"></a>你想知道更多

- [視窗樣式](../mfc/reference/styles-used-by-mfc.md#window-styles)

- [框架視窗樣式](../mfc/frame-window-styles-cpp.md)

- [視窗樣式](/windows/win32/winmsg/window-styles)

## <a name="see-also"></a>另請參閱

[框架視窗樣式](../mfc/frame-window-styles-cpp.md)
