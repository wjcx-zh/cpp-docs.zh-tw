---
title: 輸出(裝置內容) 類別
ms.date: 11/04/2016
f1_keywords:
- vc.classes.output
helpviewer_keywords:
- device contexts [MFC], classes
- screen output classes [MFC]
- printing classes [MFC]
- window drawing classes [MFC]
- painting classes [MFC]
- output classes [MFC]
ms.assetid: 35fd6435-a38e-42c6-a3fa-cd6f39370fc3
ms.openlocfilehash: 1d76570e7bfd4ce587b3803235394ec5406d30b2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266649"
---
# <a name="output-device-context-classes"></a>輸出(裝置內容) 類別

這些類別會封裝的各種不同裝置在 Windows 中可用的內容。

大部分的下列類別會封裝 Windows 裝置內容控制代碼。 裝置內容是 Windows 物件，其中包含的顯示器或印表機等裝置的繪製屬性的相關資訊。 所有的繪製呼叫都會經過裝置內容物件。 其他類別衍生自`CDC`封裝特製化的裝置內容的功能，包括 Windows 中繼檔的支援。

[CDC](../mfc/reference/cdc-class.md)<br/>
裝置內容基底類別。 使用直接存取整個顯示以及存取 nondisplay 內容，例如印表機。

[CPaintDC](../mfc/reference/cpaintdc-class.md)<br/>
中所使用的顯示內容`OnPaint`windows 的成員函式。 會自動呼叫`BeginPaint`上建構和`EndPaint`解構。

[CClientDC](../mfc/reference/cclientdc-class.md)<br/>
Windows 用戶端區域顯示內容。 例如，用來繪製滑鼠事件的立即回應中。

[CWindowDC](../mfc/reference/cwindowdc-class.md)<br/>
整個 windows，包括用戶端 」 和 「 非工作區顯示內容。

[CMetaFileDC](../mfc/reference/cmetafiledc-class.md)<br/>
Windows 中繼檔裝置內容。 Windows 中繼檔包含一連串的一種可以重新執行，以建立映像的圖形裝置介面 (GDI) 命令。 成員函式的呼叫`CMetaFileDC`中繼檔中記錄。

## <a name="related-classes"></a>相關的類別

[CPoint](../atl-mfc-shared/reference/cpoint-class.md)<br/>
保存 (x, y) 座標組。

[CSize](../atl-mfc-shared/reference/csize-class.md)<br/>
保存距離、相對位置或配對的值。

[CRect](../atl-mfc-shared/reference/crect-class.md)<br/>
保存矩形區域的座標。

[CRgn](../mfc/reference/crgn-class.md)<br/>
封裝 GDI 區域來操作的橢圓形、 多邊形，或異常的區域，在範圍內。 在類別中的裁剪成員函式搭配使用`CDC`。

[CRectTracker](../mfc/reference/crecttracker-class.md)<br/>
會顯示，並處理調整大小和移動矩形物件的使用者介面。

[CColorDialog](../mfc/reference/ccolordialog-class.md)<br/>
提供標準的對話方塊中選取一種色彩。

[CFontDialog](../mfc/reference/cfontdialog-class.md)<br/>
提供標準的對話方塊中選取的字型。

[CPrintDialog](../mfc/reference/cprintdialog-class.md)<br/>
提供標準對話方塊，來列印檔案。

## <a name="see-also"></a>另請參閱

[類別概觀](../mfc/class-library-overview.md)
