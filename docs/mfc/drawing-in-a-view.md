---
title: 在檢視中繪圖
ms.date: 11/04/2016
helpviewer_keywords:
- drawing [MFC], in views
- views [MFC], printing
- views [MFC], updating
- printing [MFC], views
- views [MFC], rendering
- printing views [MFC]
- paint messages in view class [MFC]
- device contexts, screen drawings
ms.assetid: e3761db6-0f19-4482-a4cd-ac38ef7c4d3a
ms.openlocfilehash: 227c4614bad42706893301c69882c3f40af12e2f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214340"
---
# <a name="drawing-in-a-view"></a>在檢視中繪圖

幾乎應用程式中的所有繪圖都會出現在視圖的 `OnDraw` 成員函式中，您必須在 view 類別中覆寫這個函式。 （這是滑鼠繪製的例外狀況，如[透過視圖來解讀使用者輸入](../mfc/interpreting-user-input-through-a-view.md)中所討論）。您的 `OnDraw` 覆寫：

1. 藉由呼叫您提供的檔成員函式來取得資料。

1. 藉由呼叫架構傳遞給 `OnDraw`之裝置內容物件的成員函式，來顯示資料。

當檔的資料以某種方式變更時，必須重新繪製此視圖以反映變更。 通常當使用者透過檔的視圖進行變更時，就會發生這種情況。 在此情況下，view 會呼叫檔的[UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews)成員函式，以通知相同檔上的所有視圖，以自行更新。 `UpdateAllViews` 會呼叫每個 view 的[OnUpdate](../mfc/reference/cview-class.md#onupdate)成員函式。 預設的 `OnUpdate` 執行會使視圖的整個工作區失效。 您可以覆寫它，使工作區中對應至已修改檔部分的區域失效。

類別的 `UpdateAllViews` 成員函式 `CDocument` 和類別 `CView` 的 `OnUpdate` 成員函式，可讓您傳遞描述檔中哪些部分已修改的資訊。 這個「提示」機制可讓您限制視圖必須重繪的區域。 `OnUpdate` 接受兩個「提示」引數。 第一個（ *lHint*）類型為**LPARAM**，可讓您傳遞任何您喜歡的資料，而第二個*pHint*（類型 `CObject`*）可讓您將指標傳遞給衍生自 `CObject`的任何物件。

當 view 變成無效時，Windows 會將**WM_PAINT**訊息傳送給它。 View 的[OnPaint](../mfc/reference/cwnd-class.md#onpaint)處理常式函式會藉由建立[CPaintDC](../mfc/reference/cpaintdc-class.md)類別的裝置內容物件來回應訊息，並呼叫您的 view `OnDraw` 成員函式。 您通常不需要撰寫覆寫的 `OnPaint` 處理常式函式。

[裝置內容](../mfc/device-contexts.md)是一種 Windows 資料結構，其中包含裝置繪製屬性的相關資訊，例如顯示或印表機。 所有繪圖呼叫都是透過裝置內容物件進行。 若要在螢幕上繪製，`OnDraw` 會傳遞 `CPaintDC` 物件。 在印表機上繪製時，會將針對目前印表機所設定的[CDC](../mfc/reference/cdc-class.md)物件傳遞給它。

您在此視圖中繪製的程式碼會先取得檔的指標，然後透過裝置內容進行繪圖呼叫。 下列簡單的 `OnDraw` 範例說明程式：

[!code-cpp[NVC_MFCDocView#1](../mfc/codesnippet/cpp/drawing-in-a-view_1.cpp)]

在此範例中，您會將 `GetData` 函式定義為衍生檔類別的成員。

此範例會列印從檔中取得的任何字串，並以視圖為中心。 如果 `OnDraw` 呼叫是用於螢幕繪製，則在*pDC*中傳遞的 `CDC` 物件就是已經呼叫了 `BeginPaint`的 `CPaintDC`。 繪製函式的呼叫是透過裝置內容指標來進行。 如需裝置內容和繪製呼叫的詳細資訊，請參閱*MFC 參考*中的類別[CDC](../mfc/reference/cdc-class.md)和[使用視窗物件](../mfc/working-with-window-objects.md)。

如需如何撰寫 `OnDraw`的更多範例，請參閱[MFC 範例](../overview/visual-cpp-samples.md#mfc-samples)。

## <a name="see-also"></a>另請參閱

[使用檢視](../mfc/using-views.md)
