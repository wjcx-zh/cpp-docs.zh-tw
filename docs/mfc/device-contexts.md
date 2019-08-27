---
title: 裝置內容
ms.date: 11/04/2016
helpviewer_keywords:
- OnPrepareDC method [MFC]
- windows [MFC], and device context
- drawing [MFC], device context
- CClientDC class [MFC], and GetDC method [MFC]
- drawing [MFC], in mouse and device contexts
- CDC class [MFC], objects
- device contexts [MFC]
- client areas
- CMetaFileDC class [MFC], and OnPrepareDC method [MFC]
- GDI objects [MFC], device contexts
- graphic objects [MFC], device contexts
- frame windows [MFC], device contexts
- metafiles and device contexts
- EndPaint method [MFC]
- printers [MFC], device contexts
- mouse [MFC], drawing and device contexts
- BeginPaint method, CPaintDC
- CPaintDC class [MFC], device context for painting
- windows [MFC], drawing directly into
- client areas, and device context
- device contexts [MFC], CDC class [MFC]
- user interface [MFC], device contexts
- device-independent drawing
- GetDC method and CClientDC class [MFC]
- CClientDC class [MFC], and ReleaseDC method [MFC]
- ReleaseDC method [MFC]
- device contexts [MFC], about device contexts
- drawing [MFC], directly into windows
- painting and device context
ms.assetid: d0cd51f1-f778-4c7e-bf50-d738d10433c7
ms.openlocfilehash: d5337e8d8b83a641458a15612803feeec3b6361c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508665"
---
# <a name="device-contexts"></a>裝置內容

裝置內容是一種 Windows 資料結構, 其中包含裝置繪製屬性的相關資訊, 例如顯示或印表機。 所有繪圖呼叫都是透過裝置內容物件來進行, 該物件會封裝用於繪製線條、圖形和文字的 Windows Api。 裝置內容允許 Windows 中的裝置獨立繪圖。 裝置內容可以用來繪製到螢幕、印表機或中繼檔。

[CPaintDC](../mfc/reference/cpaintdc-class.md)物件會封裝常見的 Windows 用法, 呼叫`BeginPaint`函式, 然後在裝置內容中繪製`EndPaint` , 然後呼叫函式。 此`CPaintDC`函式`BeginPaint`會為您呼叫, 而析構`EndPaint`函數會呼叫。 簡化的程式是建立[CDC](../mfc/reference/cdc-class.md)物件、繪製, 然後`CDC`終結物件。 在架構中, 大部分的程式甚至都是自動化的。 特別是, 您`OnDraw`的函式會`CPaintDC`通過已備妥`OnPrepareDC`的 (via), 而您只需要在其中進行繪製。 它會由架構終結, 而基礎裝置內容會在從函式的呼叫`OnDraw`傳回時, 發行至 Windows。

[CClientDC](../mfc/reference/cclientdc-class.md)物件會封裝使用僅代表視窗工作區的裝置內容。 此`CClientDC`函式會`GetDC`呼叫函數, `ReleaseDC`而此析構函數會呼叫函式。 [CWindowDC](../mfc/reference/cwindowdc-class.md)物件會封裝代表整個視窗的裝置內容, 包括其框架。

[CMetaFileDC](../mfc/reference/cmetafiledc-class.md)物件會將繪圖封裝成 Windows 中繼檔。 與傳遞給`OnDraw`的`CPaintDC`不同, 在此情況下, 您必須自行呼叫[OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) 。

## <a name="mouse-drawing"></a>滑鼠繪製

在架構程式中, 大部分的繪圖 (也就是大部分的裝置內容工作) 都是在`OnDraw`此視圖的成員函式中完成。 不過, 您仍然可以將裝置內容物件用於其他用途。 例如, 若要針對視圖中的滑鼠移動提供追蹤意見反應, 您必須直接在視圖中繪製, 而不`OnDraw`需要等候呼叫。

在這種情況下, 您可以使用[CClientDC](../mfc/reference/cclientdc-class.md)裝置內容物件, 直接在視圖中繪製。

### <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [裝置內容 (定義)](/windows/win32/gdi/device-contexts)

- [在檢視中繪圖](../mfc/drawing-in-a-view.md)

- [透過檢視解譯使用者輸入](../mfc/interpreting-user-input-through-a-view.md)

- [線條和曲線](/windows/win32/gdi/lines-and-curves)

- [填滿的圖案](/windows/win32/gdi/filled-shapes)

- [字型和文字](/windows/win32/gdi/fonts-and-text)

- [色彩](/windows/win32/gdi/colors)

- [座標空間和轉換](/windows/win32/gdi/coordinate-spaces-and-transformations)

## <a name="see-also"></a>另請參閱

[視窗物件](../mfc/window-objects.md)
