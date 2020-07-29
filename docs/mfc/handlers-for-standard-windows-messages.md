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
ms.openlocfilehash: d967341cdb0197f1157ab9d253072f3d0d7aa46f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223144"
---
# <a name="handlers-for-standard-windows-messages"></a>標準 Windows 訊息的處理常式

標準 Windows 訊息（**WM_**）的預設處理常式是在類別中預先定義的 `CWnd` 。 類別庫以訊息名稱作為這些處理常式的基礎。 例如， **WM_PAINT**訊息的處理常式會在中宣告 `CWnd` 為：

`afx_msg void OnPaint();`

**Afx_msg**關鍵字會藉 **`virtual`** 由區別其他成員函式的處理常式，來建議 c + + 關鍵字的效果 `CWnd` 。 不過，請注意，這些函式不是真實運作，它們是透過訊息對應實作。 訊息對應完全取決於標準前置處理器巨集，而不是 C++ 語言的任何擴充功能。 **Afx_msg**關鍵字會解析為前置處理後的空白字元。

若要覆寫基底類別中定義的處理常式，只需用您的衍生類別中的相同原型定義函式，並製作處理常式的訊息對應項目即可。 您的處理常式會「覆寫」您類別的基底類別中名稱相同的任何處理常式。

在某些情況下，處理常式應該呼叫基底類別中被覆寫的處理常式，讓基底類別和 Windows 能對訊息產生作用。 有關在何處呼叫覆寫的基底類別處理常式，端視情況而定。 有時，您必須先呼叫基底類別處理常式，有時最後才呼叫。 如果您選擇不自行處理訊息，有時您會有條件地呼叫基底類別處理常式。 有時您應該呼叫基底類別處理常式，然後根據基底類別處理常式傳回的值或狀態，有條件地執行您自己的處理常式程式碼。

> [!CAUTION]
> 如果您想要將它們傳遞給基底類別處理常式，修改傳遞至處理常式的引數並不安全。 例如，您可能會想要修改處理常式的*nChar*引數 `OnChar` （例如，轉換成大寫）。 這種行為相當模糊，但如果您需要完成此效果，請改用 `CWnd` 成員函式 `SendMessage` 。

當[類別 Wizard](reference/mfc-class-wizard.md)針對指定的訊息寫入處理常式函式的基本架構時，如何判斷覆寫指定訊息的適當方式— `OnCreate` 例如， **WM_CREATE**的處理常式，以建議的覆寫成員函式的形式進行草圖。 下列範例會建議處理常式先呼叫基類處理常式，並只在其未傳回-1 的條件下繼續。

[!code-cpp[NVC_MFCMessageHandling#3](codesnippet/cpp/handlers-for-standard-windows-messages_1.cpp)]

依照慣例，這些處理常式名稱是以「On」前置詞開頭。 其中一些處理常式不接受引數，而其他則接受數個引數。 有些也具有以外的傳回型別 **`void`** 。 所有**WM_** 訊息的預設處理常式都會記錄在*MFC 參考*中，做為 `CWnd` 名稱開頭為 "On" 之類別的成員函式。 中的成員函式宣告 `CWnd` 前面會加上**afx_msg**。

## <a name="see-also"></a>另請參閱

[宣告訊息處理函式](declaring-message-handler-functions.md)
