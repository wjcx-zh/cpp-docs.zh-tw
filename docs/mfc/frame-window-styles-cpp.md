---
title: 框架視窗樣式 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- window styles [MFC]
- PreCreateWindow method, setting window styles
- windows [MFC], MFC
- frame windows [MFC], styles
- MFC, frame windows
- styles [MFC], windows
ms.assetid: fc5058c1-eec8-48d8-9f76-3fc01cfa53f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7f0e4bde874fc563535b661108cb68edefd8d977
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385010"
---
# <a name="frame-window-styles-c"></a>框架視窗樣式 (C++)

您取得 framework 框架視窗也適用於大部分的程式，但您可以使用進階的函式來取得額外的彈性[PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow) MFC 全域函式和[AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass). `PreCreateWindow` 是的成員函式`CWnd`。

如果您套用**WS_HSCROLL**並**WS_VSCROLL**主框架視窗樣式，它們會改為套用至**MDICLIENT**視窗，讓使用者能捲動**MDICLIENT**區域。

如果視窗**FWS_ADDTOTITLE**樣式位元設定 （其預設值），檢視可以得知在框架視窗標題為何，若要檢視的文件名稱為基礎的視窗的標題列中顯示。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [管理 MDI 子視窗 (MDICLIENT)](../mfc/managing-mdi-child-windows.md)，內包含的 MDI 子視窗的 MDI 框架視窗

- [變更 MFC 所建立之視窗的樣式](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)

- [視窗樣式](../mfc/reference/styles-used-by-mfc.md#window-styles)

## <a name="see-also"></a>另請參閱

[框架視窗](../mfc/frame-windows.md)

