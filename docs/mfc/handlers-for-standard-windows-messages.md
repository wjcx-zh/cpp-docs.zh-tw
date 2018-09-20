---
title: 標準 Windows 訊息的處理常式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- afx_msg
dev_langs:
- C++
helpviewer_keywords:
- Windows messages [MFC], handlers
- message handling [MFC], Windows message handlers
- handler functions, standard Windows messages
- functions [MFC], handler
- messages [MFC], Windows
ms.assetid: 19412a8b-2c38-4502-81da-13c823c7e36c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4c74e97d8b89a72fc49f41b8c7e1bf90da2ba06c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417809"
---
# <a name="handlers-for-standard-windows-messages"></a>標準 Windows 訊息的處理常式

預設的標準 Windows 訊息的處理常式 (**WM_**) 預先定義的類別中`CWnd`。 類別庫以訊息名稱作為這些處理常式的基礎。 例如，處理常式**WM_PAINT**訊息中宣告`CWnd`為：

`afx_msg void OnPaint();`

**Afx_msg**關鍵字建議影響的 c + +**虛擬**藉由區分處理常式與其他關鍵字`CWnd`成員函式。 不過，請注意，這些函式不是真實運作，它們是透過訊息對應實作。 訊息對應完全取決於標準前置處理器巨集，而不是 C++ 語言的任何擴充功能。 **Afx_msg**前置處理後關鍵字會解析為泛空白字元。

若要覆寫基底類別中定義的處理常式，只需用您的衍生類別中的相同原型定義函式，並製作處理常式的訊息對應項目即可。 您的處理常式會「覆寫」您類別的基底類別中名稱相同的任何處理常式。

在某些情況下，處理常式應該呼叫基底類別中被覆寫的處理常式，讓基底類別和 Windows 能對訊息產生作用。 有關在何處呼叫覆寫的基底類別處理常式，端視情況而定。 有時，您必須先呼叫基底類別處理常式，有時最後才呼叫。 如果您選擇不自行處理訊息，有時您會有條件地呼叫基底類別處理常式。 有時您應該呼叫基底類別處理常式，然後根據基底類別處理常式傳回的值或狀態，有條件地執行您自己的處理常式程式碼。

> [!CAUTION]
>  如果您想要將它們傳遞給基底類別處理常式，修改傳遞至處理常式的引數並不安全。 例如，您可能會想要修改*nChar*引數`OnChar`處理常式 (要轉換為大寫，例如)。 此行為相當不清楚，但是，如果您需要完成此效果，請使用`CWnd`成員函式`SendMessage`改。

您該如何判斷適當的方式，來覆寫指定的訊息，當 [屬性] 視窗將寫入指定的訊息處理常式函式的基本架構 —`OnCreate`處理常式**WM_CREATE**，比方說，它的形式描繪建議的覆寫的成員函式。 下列範例建議處理常式先呼叫基底類別處理常式，並繼續進行 僅在情況，它不會傳回-1。

[!code-cpp[NVC_MFCMessageHandling#3](../mfc/codesnippet/cpp/handlers-for-standard-windows-messages_1.cpp)]

依照慣例，這些處理常式名稱是以「On」前置詞開頭。 其中一些處理常式不接受引數，而其他則接受數個引數。 有些也有傳回型別以外**void**。 所有的預設處理常式**WM_** 訊息所述*MFC 參考 》* 類別成員函式為`CWnd`名稱開頭為 [開啟]。 中的成員函式宣告`CWnd`前面會加上**afx_msg**。

## <a name="see-also"></a>另請參閱

[宣告訊息處理函式](../mfc/declaring-message-handler-functions.md)
