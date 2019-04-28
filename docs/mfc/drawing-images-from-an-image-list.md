---
title: 從影像清單描繪影像
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], drawing images from
- drawing [MFC], images from image lists
- image lists [MFC], drawing images from
- images [MFC], drawing
ms.assetid: 2f6063fb-1c28-45f8-a333-008c064db11c
ms.openlocfilehash: e2058c727620c9aae4ccd9a3fbeaae02c78ce8c6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62262797"
---
# <a name="drawing-images-from-an-image-list"></a>從影像清單描繪影像

若要繪製影像，請使用[cimagelist:: Draw](../mfc/reference/cimagelist-class.md#draw)成員函式。 您將會指定裝置內容物件指標、繪製之影像索引、裝置內容中要繪製影像的位置，以及指出繪製樣式的一組旗標。

當您指定**ILD_TRANSPARENT**樣式，`Draw`使用雙步驟的程序繪製遮罩的影像。 首先，它會在影像位元和遮罩位元執行邏輯 AND 作業。 然後，它會在第一個作業的結果與目的裝置内容的背景位元，執行邏輯 XOR 作業。 這個程序會在產生的影像中建立透明區域，即遮罩中每個白色位元會使產生影像的對應位元變成透明。

之前在單色背景繪製遮罩的影像，您應該使用[SetBkColor](../mfc/reference/cimagelist-class.md#setbkcolor)成員函式做為目的地相同的色彩設定的影像清單的背景色彩。 設定色彩就不需要的映像中建立透明區域，並讓`Draw`，只是將映像複製到目的地裝置內容，導致效能大幅提升。 若要繪製影像，指定**ILD_NORMAL**樣式，當您呼叫`Draw`。

您可以設定遮罩的影像清單的背景色彩 ([CImageList](../mfc/reference/cimagelist-class.md)) 在任何時間，讓它正確繪製於任何單色背景。 若要設定的背景色彩**CLR_NONE**導致預設會以透明方式繪製的映像。 若要擷取的映像清單的背景色彩，請使用[GetBkColor](../mfc/reference/cimagelist-class.md#getbkcolor)成員函式。

**ILD_BLEND25**並**ILD_BLEND50**樣式遞色系統反白顯示色彩與影像。 如果您使用代表使用者可選取之物件的遮罩影像，這些樣式便可派上用場。 例如，您可以使用**ILD_BLEND50**樣式來繪製影像，當使用者選取它。

將非遮罩的影像複製到目的地裝置內容中使用`SRCCOPY`點陣作業。 不論裝置內容的背景色彩為何，影像色彩都與之相同。 在指定的繪製樣式`Draw`也有 將非遮罩影像外觀產生任何作用。

Draw 成員函式，另一個函式，除了[DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect)，呈現影像的能力。 `DrawIndirect` 時間越長，做為參數， [2&AMP;GT;IMAGELISTDRAWPARAMS&AMP;LT;2](/windows/desktop/api/commctrl/ns-commctrl-_imagelistdrawparams)結構。 這個結構可以用來自訂目前影像的呈現，包括使用點陣化操作 (ROP) 程式碼。 如需 ROP 程式碼的詳細資訊，請參閱[點陣作業程式碼](/windows/desktop/gdi/raster-operation-codes)並[點陣圖當做筆刷](/windows/desktop/gdi/bitmaps-as-brushes)Windows SDK 中。

## <a name="see-also"></a>另請參閱

[使用 CImageList](../mfc/using-cimagelist.md)<br/>
[控制項](../mfc/controls-mfc.md)
