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
ms.openlocfilehash: b15f5034604f9d6b67574288140b79b144692478
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615366"
---
# <a name="output-device-context-classes"></a>輸出(裝置內容) 類別

這些類別會封裝 Windows 中可用的不同類型的裝置內容。

下列大部分類別都會將控制碼封裝到 Windows 裝置內容。 裝置內容是 Windows 物件，其中包含裝置的繪圖屬性相關資訊，例如顯示或印表機。 所有繪圖呼叫都是透過裝置內容物件進行。 衍生自的其他類別會 `CDC` 封裝特定的裝置內容功能，包括對 Windows 中繼檔的支援。

[CDC](reference/cdc-class.md)<br/>
裝置內容的基類。 直接用來存取整個顯示器和存取 nondisplay 內容，例如印表機。

[CPaintDC](reference/cpaintdc-class.md)<br/>
在 windows 的成員函式中使用的顯示內容 `OnPaint` 。 會自動呼叫 `BeginPaint` 結構上和 `EndPaint` 損毀。

[CClientDC](reference/cclientdc-class.md)<br/>
Windows 用戶端區域的顯示內容。 例如，用來以立即回應的方式繪製滑鼠事件。

[CWindowDC](reference/cwindowdc-class.md)<br/>
整個視窗的顯示內容，包括用戶端和非工作區。

[CMetaFileDC](reference/cmetafiledc-class.md)<br/>
Windows 中繼檔的裝置內容。 Windows 中繼檔包含一連串的圖形裝置介面（GDI）命令，可以重新執行以建立映射。 對的成員函式所做的呼叫 `CMetaFileDC` 會記錄在中繼檔中。

## <a name="related-classes"></a>相關類別

[CPoint](../atl-mfc-shared/reference/cpoint-class.md)<br/>
保存 (x, y) 座標組。

[CSize](../atl-mfc-shared/reference/csize-class.md)<br/>
保存距離、相對位置或配對的值。

[CRect](../atl-mfc-shared/reference/crect-class.md)<br/>
保存矩形區域的座標。

[CRgn](reference/crgn-class.md)<br/>
封裝 GDI 區域，用於操作視窗內的橢圓形、多邊形或不規則區域。 與類別中的裁剪成員函式搭配使用 `CDC` 。

[CRectTracker](reference/crecttracker-class.md)<br/>
顯示和處理用來調整大小和移動矩形物件的使用者介面。

[CColorDialog](reference/ccolordialog-class.md)<br/>
提供用來選取色彩的標準對話方塊。

[CFontDialog](reference/cfontdialog-class.md)<br/>
提供用來選取字型的標準對話方塊。

[CPrintDialog](reference/cprintdialog-class.md)<br/>
提供用來列印檔案的標準對話方塊。

## <a name="see-also"></a>另請參閱

[類別概觀](class-library-overview.md)
