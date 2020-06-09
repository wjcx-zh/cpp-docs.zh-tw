---
title: 框架視窗樣式 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- window styles [MFC]
- PreCreateWindow method, setting window styles
- windows [MFC], MFC
- frame windows [MFC], styles
- MFC, frame windows
- styles [MFC], windows
ms.assetid: fc5058c1-eec8-48d8-9f76-3fc01cfa53f7
ms.openlocfilehash: 3c22944537370a44aee1af1cf71281264ed4969b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626461"
---
# <a name="frame-window-styles-c"></a>框架視窗樣式 (C++)

您使用此架構取得的框架視窗適用于大部分的程式，但您可以使用 [advanced 函數[PreCreateWindow](reference/cwnd-class.md#precreatewindow) ] 和 [MFC 全域函式[AfxRegisterWndClass](reference/application-information-and-management.md#afxregisterwndclass)] 來取得額外的彈性。 `PreCreateWindow`是的成員函式 `CWnd` 。

如果您將**WS_HSCROLL**和**WS_VSCROLL**樣式套用到主框架視窗，則會改為將它們套用至**MDICLIENT**視窗，讓使用者可以滾動**MDICLIENT**區域。

如果已設定視窗的**FWS_ADDTOTITLE**樣式位（預設值），則此視圖會根據視圖的檔案名稱，告訴框架視窗要在視窗標題列中顯示的標題。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [管理 mdi 子視窗（MDICLIENT）](managing-mdi-child-windows.md)，mdi 框架內包含 mdi 子視窗的視窗

- [變更 MFC 所建立之視窗的樣式](changing-the-styles-of-a-window-created-by-mfc.md)

- [視窗樣式](reference/styles-used-by-mfc.md#window-styles)

## <a name="see-also"></a>另請參閱

[框架視窗](frame-windows.md)
