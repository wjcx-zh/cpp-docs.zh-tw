---
title: "訊息對應 (MFC) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.messages
dev_langs:
- C++
helpviewer_keywords:
- message maps [C++], MFC
- Windows messages [C++], message maps
- messages [C++], Windows
- MFC [C++], messages
ms.assetid: 3f9855e4-9d7d-4b64-8f3f-a19ea3cf79ba
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: bb31d35e221c9f5d06dc34408bed500b4a18b077
ms.lasthandoff: 02/24/2017

---
# <a name="message-maps-mfc"></a>訊息對應 (MFC)
參考的這個區段會列出所有[訊息對應巨集](../../mfc/reference/message-map-macros-mfc.md)和所有[CWnd](../../mfc/reference/cwnd-class.md)訊息對應項目，以及相對應的成員函式原型︰  
  
|分類|說明|  
|--------------|-----------------|  
|[WM_COMMAND 訊息處理常式](../../mfc/reference/wm-command-message-handler.md)|處理**WM_COMMAND**使用者功能表選取項目或功能表便捷鍵所產生的訊息。|  
|[子視窗通知訊息處理常式](../../mfc/reference/child-window-notification-message-handlers.md)|處理從子視窗通知訊息。|  
|[WM_ 訊息處理常式](../../mfc/reference/handlers-for-wm-messages.md)|處理**WM_**訊息，例如`WM_PAINT`。|  
|[使用者定義的訊息處理常式](../../mfc/reference/user-defined-handlers.md)|處理使用者定義的訊息。|  
  
 (如術語和這個參考所使用的慣例的說明，請參閱[如何使用訊息對應交互參考](../../mfc/reference/how-to-use-the-message-map-cross-reference.md)。)  
  
 由於 Windows 是訊息導向的作業系統，大部分的 Windows 環境的程式設計包含訊息處理。 每次按一下按鍵或滑鼠等事件發生時，將訊息傳送至應用程式，然後必須處理事件。  
  
 Mfc 程式庫提供的訊息為基礎的程式設計最佳化的程式設計模型。 在此模型中，「 訊息對應 」 用來指定哪些函式會處理特定類別的各種訊息。 訊息對應包含一或多個指定的訊息會由哪些函式的巨集。 例如，一個訊息對應，其中包含`ON_COMMAND`巨集看起來可能像這樣︰  
  
 [!code-cpp[NVC_MFCMessageMaps #&16;](../../mfc/reference/codesnippet/cpp/message-maps-mfc_1.cpp)]  
  
 `ON_COMMAND`巨集用來處理產生的功能表、 按鈕和快速鍵的命令訊息。 [巨集](../../mfc/reference/message-map-macros-mfc.md)可供對應下列︰  
  
## <a name="windows-messages"></a>Windows 訊息  
  
-   控制項告知  
  
-   使用者定義的訊息  
  
## <a name="command-messages"></a>命令訊息  
  
-   已註冊的使用者定義訊息  
  
-   使用者介面更新訊息  
  
## <a name="ranges-of-messages"></a>訊息的範圍  
  
-   命令  
  
-   更新處理常式的訊息  
  
-   控制項告知  
  
 雖然訊息對應巨集很重要，但您通常不需要直接使用它們。 這是因為 [屬性] 視窗時，自動建立訊息對應項目在原始程式檔中您用它來將訊息處理函式與訊息產生關聯。 每當您想要編輯或加入訊息對應項目，您可以使用 [屬性] 視窗。  
  
> [!NOTE]
>  [屬性] 視窗不支援訊息對應範圍。 您必須自行撰寫這些訊息對應項目。  
  
 不過，訊息對應的 Mfc 程式庫的重要部分。 您應該了解他們做什麼，並為其提供文件。  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)


