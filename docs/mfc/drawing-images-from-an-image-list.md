---
title: 從影像清單描繪影像 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CImageList class [MFC], drawing images from
- drawing [MFC], images from image lists
- image lists [MFC], drawing images from
- images [MFC], drawing
ms.assetid: 2f6063fb-1c28-45f8-a333-008c064db11c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 86983506770b9719972170dfbb70b02c8026e108
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="drawing-images-from-an-image-list"></a>從影像清單描繪影像
若要繪製影像，請使用[cimagelist:: Draw](../mfc/reference/cimagelist-class.md#draw)成員函式。 您將會指定裝置內容物件指標、繪製之影像索引、裝置內容中要繪製影像的位置，以及指出繪製樣式的一組旗標。  
  
 當您指定`ILD_TRANSPARENT`樣式，**繪製**使用兩步驟程序繪製遮罩的影像。 首先，它會在影像位元和遮罩位元執行邏輯 AND 作業。 然後，它會在第一個作業的結果與目的裝置内容的背景位元，執行邏輯 XOR 作業。 這個程序會在產生的影像中建立透明區域，即遮罩中每個白色位元會使產生影像的對應位元變成透明。  
  
 之前為單色背景繪製遮罩的影像，您應該使用[SetBkColor](../mfc/reference/cimagelist-class.md#setbkcolor)成員函式的影像清單的背景色彩設定為相同的色彩做為目的地。 設定色彩不需要在影像中建立透明區域，並讓**繪製**只複製映像的目的地裝置內容，導致效能大幅提升。 若要繪製影像，指定`ILD_NORMAL`樣式，當您呼叫**繪製**。  
  
 您可以設定遮罩的影像清單的背景色彩 ([CImageList](../mfc/reference/cimagelist-class.md)) 在任何時間，讓它正確繪製於任何單色背景。 將背景色彩設定為 `CLR_NONE`，會導致影像預設繪製成透明。 若要擷取影像清單的背景色彩，請使用[GetBkColor](../mfc/reference/cimagelist-class.md#getbkcolor)成員函式。  
  
 使用系統醒目提示色彩為影像進行 `ILD_BLEND25` 和 `ILD_BLEND50` 樣式遞色。 如果您使用代表使用者可選取之物件的遮罩影像，這些樣式便可派上用場。 例如，您可以使用由使用者選取的 `ILD_BLEND50` 樣式來繪製影像。  
  
 將非遮罩的影像複製到目的地裝置內容中使用**SRCCOPY**點陣作業。 不論裝置內容的背景色彩為何，影像色彩都與之相同。 在指定的繪製樣式**繪製**也有非遮罩影像外觀產生任何作用。  
  
 除了繪製成員函式，另一個函式， [DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect)，呈現影像的能力。 `DrawIndirect` 時間越長，做為參數， [IMAGELISTDRAWPARAMS](http://msdn.microsoft.com/library/windows/desktop/bb761395)結構。 這個結構可以用來自訂目前影像的呈現，包括使用點陣化操作 (ROP) 程式碼。 如需有關 ROP 代碼的詳細資訊，請參閱[點陣作業程式碼](http://msdn.microsoft.com/library/windows/desktop/dd162892)和[點陣圖另存為筆刷](http://msdn.microsoft.com/library/windows/desktop/dd183378)Windows SDK 中。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CImageList](../mfc/using-cimagelist.md)   
 [控制項](../mfc/controls-mfc.md)

