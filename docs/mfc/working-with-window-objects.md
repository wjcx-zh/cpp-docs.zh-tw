---
title: 使用視窗物件
ms.date: 11/04/2016
helpviewer_keywords:
- child windows [MFC], working with
- window objects [MFC], working with
ms.assetid: f73aa254-90e3-46a9-8e9b-d78b7054a331
ms.openlocfilehash: 66656fceec2005f7e789bf1cd68ffe52651aacc7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50526531"
---
# <a name="working-with-window-objects"></a>使用視窗物件

使用的兩種類型的活動視窗呼叫：

- 處理 Windows 訊息

- 在視窗的繪圖

若要處理 Windows 訊息在任何視窗中，包括您自己的子視窗，請參閱[將訊息對應至函式](../mfc/reference/mapping-messages-to-functions.md)將訊息對應至您的 c + + 視窗類別。 然後撰寫訊息處理常式成員函式在您的類別。

在架構應用程式中的大部分繪圖發生在檢視中，其[OnDraw](../mfc/reference/cview-class.md#ondraw)每當必須繪製視窗的內容時，呼叫成員函式。 如果您的視窗是檢視的子系，您可能會委派部分檢視的繪圖給子視窗有`OnDraw`呼叫其中一個視窗的成員函式。

在任何情況下，您必須在裝置內容的繪圖。 您可以使用內建的畫筆、 筆刷和其他與您的視窗相關聯的裝置內容中包含的圖形物件。 或者，您可以修改這些物件，以取得您需要的繪圖效果。 您要設定的裝置內容，呼叫成員函式的類別[CDC](../mfc/reference/cdc-class.md) （裝置內容類別） 繪製線條、 圖形和文字; 使用的色彩，並使用座標系統。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [訊息處理和對應](../mfc/message-handling-and-mapping.md)

- [在檢視中繪圖](../mfc/drawing-in-a-view.md)

- [裝置內容](../mfc/device-contexts.md)

- [圖形物件](../mfc/graphic-objects.md)

## <a name="see-also"></a>另請參閱

[視窗物件](../mfc/window-objects.md)

