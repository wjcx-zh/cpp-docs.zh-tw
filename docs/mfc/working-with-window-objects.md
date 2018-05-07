---
title: 使用視窗物件 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- child windows [MFC], working with
- window objects [MFC], working with
ms.assetid: f73aa254-90e3-46a9-8e9b-d78b7054a331
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e4c00649c51e34bbbac7adbf7aa5f3c7d04790ad
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="working-with-window-objects"></a>使用視窗物件
使用的兩種類型的活動視窗呼叫：  
  
-   處理 Windows 訊息  
  
-   在視窗中的繪圖  
  
 若要處理 Windows 訊息在任何視窗中，包括您自己的子視窗，請參閱[訊息對應到函式](../mfc/reference/mapping-messages-to-functions.md)將訊息對應到您的 c + + 視窗類別。 然後訊息處理常式成員函式中寫入您的類別。  
  
 在架構應用程式中的大部分繪圖發生在檢視中，其[OnDraw](../mfc/reference/cview-class.md#ondraw)每當必須繪製視窗的內容，會呼叫成員函式。 如果您的視窗是檢視的子系，您可能會部分檢視的繪圖透過委派給子視窗有`OnDraw`呼叫其中一個視窗的成員函式。  
  
 在任何情況下，您必須在裝置內容的繪圖。 您可以使用內建的畫筆、 筆刷和其他與視窗相關聯的裝置內容中所包含的圖形物件。 或者，您可以修改這些物件來取得您需要的繪圖效果。 依您設定您的裝置內容，呼叫成員函式的類別[CDC](../mfc/reference/cdc-class.md) （裝置內容類別） 繪製線條、 圖形和文字; 使用色彩; 和搭配使用座標系統。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [訊息處理和對應](../mfc/message-handling-and-mapping.md)  
  
-   [在檢視中繪圖](../mfc/drawing-in-a-view.md)  
  
-   [裝置內容](../mfc/device-contexts.md)  
  
-   [圖形物件](../mfc/graphic-objects.md)  
  
## <a name="see-also"></a>另請參閱  
 [視窗物件](../mfc/window-objects.md)

