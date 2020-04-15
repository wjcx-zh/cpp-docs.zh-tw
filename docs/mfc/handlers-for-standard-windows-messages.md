---
title: 標準 Windows 訊息的處理常式
ms.date: 11/04/2016
f1_keywords:
- afx_msg
helpviewer_keywords:
- Windows messages [MFC], handlers
- message handling [MFC], Windows message handlers
- handler functions, standard Windows messages
- functions [MFC], handler
- messages [MFC], Windows
ms.assetid: 19412a8b-2c38-4502-81da-13c823c7e36c
ms.openlocfilehash: 9a136caf3a1d22151cb9cfd48e1cd3f999ab51ec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370493"
---
# <a name="handlers-for-standard-windows-messages"></a>標準 Windows 訊息的處理常式

標準 Windows 消息 **(WM_**)`CWnd`的預設處理程式在 類中預定義。 類別庫以訊息名稱作為這些處理常式的基礎。 例如 **,WM_PAINT**訊息的處理程式聲明`CWnd`為 :

`afx_msg void OnPaint();`

**afx_msg**關鍵字通過將處理程式與其他`CWnd`成員 函數區分開來來建議C++**虛擬**關鍵字的效果。 不過，請注意，這些函式不是真實運作，它們是透過訊息對應實作。 訊息對應完全取決於標準前置處理器巨集，而不是 C++ 語言的任何擴充功能。 **afx_msg**關鍵字在預處理后解析為空白。

若要覆寫基底類別中定義的處理常式，只需用您的衍生類別中的相同原型定義函式，並製作處理常式的訊息對應項目即可。 您的處理常式會「覆寫」您類別的基底類別中名稱相同的任何處理常式。

在某些情況下，處理常式應該呼叫基底類別中被覆寫的處理常式，讓基底類別和 Windows 能對訊息產生作用。 有關在何處呼叫覆寫的基底類別處理常式，端視情況而定。 有時，您必須先呼叫基底類別處理常式，有時最後才呼叫。 如果您選擇不自行處理訊息，有時您會有條件地呼叫基底類別處理常式。 有時您應該呼叫基底類別處理常式，然後根據基底類別處理常式傳回的值或狀態，有條件地執行您自己的處理常式程式碼。

> [!CAUTION]
> 如果您想要將它們傳遞給基底類別處理常式，修改傳遞至處理常式的引數並不安全。 例如,您可能很想修改`OnChar`處理程式的*nChar*參數(例如轉換為大寫)。 此行為相當模糊,但如果需要完成此效果,`CWnd`請使用成員函數`SendMessage`。

當[類嚮導](reference/mfc-class-wizard.md)為給定消息`OnCreate`(例如**WM_CREATE**的處理程式)編寫處理程式函數骨架時,如何確定重寫給定消息的正確方法? 以下範例建議處理程式首先調用基類處理程式,並在不返回 -1 的情況下繼續操作。

[!code-cpp[NVC_MFCMessageHandling#3](../mfc/codesnippet/cpp/handlers-for-standard-windows-messages_1.cpp)]

依照慣例，這些處理常式名稱是以「On」前置詞開頭。 其中一些處理常式不接受引數，而其他則接受數個引數。 有些也有傳回類型,而不是**無效**。 所有**WM_** 訊息的預設處理程式都記錄在*MFC 參考*中,作為名稱以"On"開頭的類`CWnd`的成員函數。 中`CWnd`的成員函數聲明以**afx_msg**為預綴。

## <a name="see-also"></a>另請參閱

[宣告訊息處理函式](../mfc/declaring-message-handler-functions.md)
