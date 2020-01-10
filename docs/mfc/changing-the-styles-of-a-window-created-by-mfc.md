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
ms.openlocfilehash: ef79fc88604d565a942fdb0ae07d5fc5a2e0ebeb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509008"
---
# <a name="changing-the-styles-of-a-window-created-by-mfc"></a>變更 MFC 所建立之視窗的樣式

在它的函式`WinMain`版本中，MFC 會為您註冊數個標準視窗類別。 因為您通常不會編輯 mfc `WinMain`，所以該函式不會有任何機會變更 mfc 預設視窗樣式。 本文說明如何在現有的應用程式中變更這類預先註冊視窗類別的樣式。

##  <a name="_core_changing_styles_in_a_new_mfc_application"></a>變更新 MFC 應用程式中的樣式

如果您使用的是C++ Visual 2.0 或更新版本，當您建立應用程式時，可以變更應用程式精靈中的預設視窗樣式。 在應用程式精靈的 [使用者介面功能] 頁面中，您可以變更主框架視窗和 MDI 子視窗的樣式。 對於任一種視窗類型，您都可以指定其框架粗細（粗或細）和下列任何一項：

- 視窗是否有最小化或最大化控制項。

- 視窗一開始是最小化、最大化，或兩者皆不出現。

針對主框架視窗，您也可以指定視窗是否有 [系統] 功能表。 若為 MDI 子視窗，您可以指定視窗是否支援分隔窗格。

##  <a name="_core_changing_styles_in_an_existing_application"></a>變更現有應用程式中的樣式

如果您要變更現有應用程式中的視窗屬性，請改為遵循本文其餘部分中的指示。

若要變更使用應用程式精靈所建立之架構應用程式所使用的預設視窗屬性，請覆寫視窗的[PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow)虛擬成員函式。 `PreCreateWindow`允許應用程式存取通常由[CDocTemplate](../mfc/reference/cdoctemplate-class.md)類別在內部管理的建立進程。 架構只會`PreCreateWindow`在建立視窗之前呼叫。 藉由修改傳遞至`PreCreateWindow`的 [CREATESTRUCT](/windows/win32/api/winuser/ns-winuser-createstructw) 結構，您的應用程式可以變更用來建立視窗的屬性。 例如，若要確保視窗不使用標題，請使用下列位運算：

[!code-cpp[NVC_MFCDocView#15](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_1.cpp)]

[CTRLBARS](../overview/visual-cpp-samples.md)範例應用程式會示範變更視窗屬性的這項技術。 根據您的`PreCreateWindow`應用程式變更的內容而定，可能需要呼叫函式的基類實作為。

下列討論涵蓋了 SDI 案例和[MDI 案例](#_core_the_mdi_case)。

##  <a name="_core_the_sdi_case"></a>SDI 案例

在單一檔介面（SDI）應用程式中，架構中的預設視窗樣式是**WS_OVERLAPPEDWINDOW**和**FWS_ADDTOTITLE**樣式的組合。 **FWS_ADDTOTITLE**是 MFC 特定的樣式，可指示架構將檔標題加入至視窗的標題。 若要變更 SDI 應用程式中的視窗屬性，請`PreCreateWindow`覆寫衍生自`CFrameWnd`之類別中的函式（應用`CMainFrame`程式嚮導名稱）。 例如：

[!code-cpp[NVC_MFCDocViewSDI#11](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_2.cpp)]

此程式碼會建立主框架視窗，而不會將按鈕最小化和最大化，而且沒有可調的框線。 視窗一開始會在螢幕上置中。

##  <a name="_core_the_mdi_case"></a>MDI 案例

在多重文件介面（MDI）應用程式中變更子視窗的視窗樣式時，需要執行更多工作。 根據預設，使用應用程式精靈所建立的 MDI 應用程式會使用 MFC 中定義的預設[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)類別。 若要變更 MDI 子視窗的視窗樣式，您必須從`CMDIChildWnd`衍生新的類別，並將專案`CMDIChildWnd`中的所有參考取代為新類別的參考。 最有可能的情況是， `CMDIChildWnd`應用程式中唯一的參考是位於應用`InitInstance`程式的成員函式中。

MDI 應用程式中使用的預設視窗樣式是**WS_CHILD**、 **WS_OVERLAPPEDWINDOW**和**FWS_ADDTOTITLE**樣式的組合。 若要變更 MDI 應用程式之子視窗的視窗屬性，請覆寫衍生自之`CMDIChildWnd`類別中的 [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow) 函式。 例如：

[!code-cpp[NVC_MFCDocView#16](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_3.cpp)]

此程式碼會建立不含 [最大化] 按鈕的 MDI 子視窗。

### <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [Windows 樣式](../mfc/reference/styles-used-by-mfc.md#window-styles)

- [框架視窗樣式](../mfc/frame-window-styles-cpp.md)

- [視窗樣式](/windows/win32/winmsg/window-styles)

## <a name="see-also"></a>另請參閱

[框架視窗樣式](../mfc/frame-window-styles-cpp.md)
