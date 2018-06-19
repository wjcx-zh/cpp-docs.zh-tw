---
title: 輸出 （裝置內容） 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.output
dev_langs:
- C++
helpviewer_keywords:
- device contexts [MFC], classes
- screen output classes [MFC]
- printing classes [MFC]
- window drawing classes [MFC]
- painting classes [MFC]
- output classes [MFC]
ms.assetid: 35fd6435-a38e-42c6-a3fa-cd6f39370fc3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 85571e2173d9dc4e900d63e982a91571fafc103e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350480"
---
# <a name="output-device-context-classes"></a>輸出(裝置內容) 類別
這些類別會封裝之不同類型的裝置在 Windows 中可用的內容。  
  
 大部分的下列類別會封裝 Windows 裝置內容的控制代碼。 裝置內容是 Windows 物件，其中包含顯示或印表機等裝置的繪圖屬性相關資訊。 所有的繪製呼叫是透過裝置內容物件。 其他類別衍生自`CDC`封裝特定的裝置內容的功能，包括 Windows 中繼檔的支援。  
  
 [CDC](../mfc/reference/cdc-class.md)  
 裝置內容的基底類別。 使用直接存取整個顯示以及存取 nondisplay 內容，例如印表機。  
  
 [CPaintDC](../mfc/reference/cpaintdc-class.md)  
 在中使用的顯示內容`OnPaint`windows 的成員函式。 會自動呼叫`BeginPaint`在建構和`EndPaint`解構時。  
  
 [CClientDC](../mfc/reference/cclientdc-class.md)  
 Windows 用戶端區域顯示內容。 例如，用來繪製滑鼠事件的立即回應中。  
  
 [CWindowDC](../mfc/reference/cwindowdc-class.md)  
 包括用戶端和非工作區的整個 windows 顯示內容。  
  
 [CMetaFileDC](../mfc/reference/cmetafiledc-class.md)  
 Windows 中繼檔裝置內容。 Windows 中繼檔包含一系列可用來重新執行來建立映像的繪圖裝置介面 (GDI) 命令。 對成員函式的呼叫`CMetaFileDC`中繼檔中記錄。  
  
## <a name="related-classes"></a>相關的類別  
 [CPoint](../atl-mfc-shared/reference/cpoint-class.md)  
 保存 (x, y) 座標組。  
  
 [CSize](../atl-mfc-shared/reference/csize-class.md)  
 保存距離、相對位置或配對的值。  
  
 [CRect](../atl-mfc-shared/reference/crect-class.md)  
 保存矩形區域的座標。  
  
 [CRgn](../mfc/reference/crgn-class.md)  
 封裝管理視窗的橢圓形、 多邊形，或不規則區域的 GDI 區域。 類別中的裁剪成員函式搭配使用`CDC`。  
  
 [CRectTracker](../mfc/reference/crecttracker-class.md)  
 會顯示，並處理調整大小和移動矩形物件的使用者介面。  
  
 [CColorDialog](../mfc/reference/ccolordialog-class.md)  
 提供的標準對話方塊選取色彩。  
  
 [CFontDialog](../mfc/reference/cfontdialog-class.md)  
 提供的標準對話方塊選取字型。  
  
 [CPrintDialog](../mfc/reference/cprintdialog-class.md)  
 列印檔案中提供的標準對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../mfc/class-library-overview.md)

