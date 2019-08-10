---
title: 從影像清單描繪影像
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], drawing images from
- drawing [MFC], images from image lists
- image lists [MFC], drawing images from
- images [MFC], drawing
ms.assetid: 2f6063fb-1c28-45f8-a333-008c064db11c
ms.openlocfilehash: e4e60f0e6e4ee22712e4bbce344fd6437cf3db7e
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916415"
---
# <a name="drawing-images-from-an-image-list"></a>從影像清單描繪影像

若要繪製影像, 請使用[CImageList::D 原始](../mfc/reference/cimagelist-class.md#draw)成員函式。 您將會指定裝置內容物件指標、繪製之影像索引、裝置內容中要繪製影像的位置，以及指出繪製樣式的一組旗標。

當您指定**ILD_TRANSPARENT**樣式時, `Draw`會使用兩個步驟的進程來繪製遮罩影像。 首先，它會在影像位元和遮罩位元執行邏輯 AND 作業。 然後，它會在第一個作業的結果與目的裝置内容的背景位元，執行邏輯 XOR 作業。 這個程序會在產生的影像中建立透明區域，即遮罩中每個白色位元會使產生影像的對應位元變成透明。

在純色背景上繪製遮罩影像之前, 您應該使用[SetBkColor](../mfc/reference/cimagelist-class.md#setbkcolor)成員函式, 將影像清單的背景色彩設定為與目的地相同的色彩。 設定色彩就不需要在影像中建立透明區域, 並可讓`Draw`只將影像複製到目的地裝置內容, 進而大幅提升效能。 若要繪製影像, 請在呼叫`Draw`時指定 ILD_NORMAL 樣式。

您可以隨時設定遮罩影像清單 ([CImageList](../mfc/reference/cimagelist-class.md)) 的背景色彩, 以便正確地在任何純色背景上繪製。 將背景色彩設定為**CLR_NONE** , 會使影像依預設會以透明方式繪製。 若要取得影像清單的背景色彩, 請使用[GetBkColor](../mfc/reference/cimagelist-class.md#getbkcolor)成員函式。

**ILD_BLEND25**和**ILD_BLEND50**樣式會以系統反白顯示色彩來仿色影像。 如果您使用代表使用者可選取之物件的遮罩影像，這些樣式便可派上用場。 例如, 當使用者選取影像時, 您可以使用**ILD_BLEND50**樣式來繪製映射。

Nonmasked 影像會使用`SRCCOPY` 「點陣」作業複製到目的地裝置內容。 不論裝置內容的背景色彩為何，影像色彩都與之相同。 中`Draw`指定的繪圖樣式也不會影響 nonmasked 影像的外觀。

除了 Draw 成員函式之外, 另一個函式[DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect)會擴充呈現影像的能力。 `DrawIndirect`以參數的形式接受[IMAGELISTDRAWPARAMS](/windows/desktop/api/commctrl/ns-commctrl-imagelistdrawparams)結構。 這個結構可以用來自訂目前影像的呈現，包括使用點陣化操作 (ROP) 程式碼。 如需 ROP 碼的詳細資訊, 請參閱點陣作業程式[代碼](/windows/desktop/gdi/raster-operation-codes)和點陣圖作為 Windows SDK 中的[筆刷](/windows/desktop/gdi/bitmaps-as-brushes)。

## <a name="see-also"></a>另請參閱

[使用 CImageList](../mfc/using-cimagelist.md)<br/>
[控制項](../mfc/controls-mfc.md)
