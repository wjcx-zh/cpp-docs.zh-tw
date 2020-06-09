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
ms.openlocfilehash: f3fd9f83112737e944d83cf00da685d81fe8b2a7
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624954"
---
# <a name="changing-the-styles-of-a-window-created-by-mfc"></a>變更 MFC 所建立之視窗的樣式

在它的函式版本中 `WinMain` ，MFC 會為您註冊數個標準視窗類別。 因為您通常不會編輯 MFC，所以該函式不會有 `WinMain` 任何機會變更 mfc 預設視窗樣式。 本文說明如何在現有的應用程式中變更這類預先註冊視窗類別的樣式。

## <a name="changing-styles-in-a-new-mfc-application"></a><a name="_core_changing_styles_in_a_new_mfc_application"></a>變更新 MFC 應用程式中的樣式

如果您使用 Visual C++ 2.0 或更新版本，當您建立應用程式時，可以變更應用程式精靈中的預設視窗樣式。 在應用程式精靈的 [使用者介面功能] 頁面中，您可以變更主框架視窗和 MDI 子視窗的樣式。 對於任一種視窗類型，您都可以指定其框架粗細（粗或細）和下列任何一項：

- 視窗是否有最小化或最大化控制項。

- 視窗一開始是最小化、最大化，或兩者皆不出現。

針對主框架視窗，您也可以指定視窗是否有 [系統] 功能表。 若為 MDI 子視窗，您可以指定視窗是否支援分隔窗格。

## <a name="changing-styles-in-an-existing-application"></a><a name="_core_changing_styles_in_an_existing_application"></a>變更現有應用程式中的樣式

如果您要變更現有應用程式中的視窗屬性，請改為遵循本文其餘部分中的指示。

若要變更使用應用程式精靈所建立之架構應用程式所使用的預設視窗屬性，請覆寫視窗的[PreCreateWindow](reference/cwnd-class.md#precreatewindow)虛擬成員函式。 `PreCreateWindow`允許應用程式存取通常由[CDocTemplate](reference/cdoctemplate-class.md)類別在內部管理的建立進程。 架構只會在 `PreCreateWindow` 建立視窗之前呼叫。 藉由修改傳遞至的[CREATESTRUCT](/windows/win32/api/winuser/ns-winuser-createstructw)結構 `PreCreateWindow` ，您的應用程式可以變更用來建立視窗的屬性。 例如，若要確保視窗不使用標題，請使用下列位運算：

[!code-cpp[NVC_MFCDocView#15](codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_1.cpp)]

[CTRLBARS](../overview/visual-cpp-samples.md)範例應用程式會示範變更視窗屬性的這項技術。 根據您的應用程式變更的內容 `PreCreateWindow` 而定，可能需要呼叫函式的基類實作為。

下列討論涵蓋了 SDI 案例和[MDI 案例](#_core_the_mdi_case)。

## <a name="the-sdi-case"></a><a name="_core_the_sdi_case"></a>SDI 案例

在單一檔介面（SDI）應用程式中，架構中的預設視窗樣式是**WS_OVERLAPPEDWINDOW**和**FWS_ADDTOTITLE**樣式的組合。 **FWS_ADDTOTITLE**是 MFC 特定的樣式，可指示架構將檔標題加入至視窗的標題。 若要變更 SDI 應用程式中的視窗屬性，請覆寫 `PreCreateWindow` 衍生自之類別中的函式 `CFrameWnd` （應用程式精靈名稱 `CMainFrame` ）。 例如：

[!code-cpp[NVC_MFCDocViewSDI#11](codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_2.cpp)]

此程式碼會建立主框架視窗，而不會將按鈕最小化和最大化，而且沒有可調的框線。 視窗一開始會在螢幕上置中。

## <a name="the-mdi-case"></a><a name="_core_the_mdi_case"></a>MDI 案例

在多重文件介面（MDI）應用程式中變更子視窗的視窗樣式時，需要執行更多工作。 根據預設，使用應用程式精靈所建立的 MDI 應用程式會使用 MFC 中定義的預設[CMDIChildWnd](reference/cmdichildwnd-class.md)類別。 若要變更 MDI 子視窗的視窗樣式，您必須從衍生新的類別， `CMDIChildWnd` 並將專案中的所有參考取代為 `CMDIChildWnd` 新類別的參考。 最有可能的 `CMDIChildWnd` 情況是，應用程式中唯一的參考是位於應用程式的成員函式中 `InitInstance` 。

MDI 應用程式中使用的預設視窗樣式是**WS_CHILD**、 **WS_OVERLAPPEDWINDOW**和**FWS_ADDTOTITLE**樣式的組合。 若要變更 MDI 應用程式之子視窗的視窗屬性，請覆寫衍生自之類別中的[PreCreateWindow](reference/cwnd-class.md#precreatewindow)函式 `CMDIChildWnd` 。 例如：

[!code-cpp[NVC_MFCDocView#16](codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_3.cpp)]

此程式碼會建立不含 [最大化] 按鈕的 MDI 子視窗。

### <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [Windows 樣式](reference/styles-used-by-mfc.md#window-styles)

- [框架視窗樣式](frame-window-styles-cpp.md)

- [視窗樣式](/windows/win32/winmsg/window-styles)

## <a name="see-also"></a>另請參閱

[框架視窗樣式](frame-window-styles-cpp.md)
