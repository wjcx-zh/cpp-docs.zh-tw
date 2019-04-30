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
ms.openlocfilehash: bc461347b56379976cdf62014507e3a15529f081
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408015"
---
# <a name="drawing-in-a-view"></a>在檢視中繪圖

在您的應用程式中的幾乎所有繪圖中的檢視，就會發生`OnDraw`成員函式，您必須在您的檢視類別中覆寫。 (例外狀況是繪製、 討論中的滑鼠[解譯使用者輸入透過檢視](../mfc/interpreting-user-input-through-a-view.md)。)您`OnDraw`覆寫：

1. 藉由呼叫成員函式，您所提供的文件中取得資料。

1. 藉由呼叫成員函式的架構會傳遞到裝置內容物件中顯示的資料`OnDraw`。

當文件的資料變更以某種方式時，必須重新繪製檢視，以反映所做的變更。 一般而言，這會發生於使用者進行變更，以透過文件的檢視。 在此情況下，檢視會呼叫文件[UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews)通知所有檢視自行更新相同的文件的成員函式。 `UpdateAllViews` 呼叫每個檢視[OnUpdate](../mfc/reference/cview-class.md#onupdate)成員函式。 預設實作`OnUpdate`失效檢視的整個工作區。 您可以覆寫它要使其失效的只有這些區域的工作區對應至文件已修改的部分。

`UpdateAllViews`類別成員函式`CDocument`並`OnUpdate`類別成員函式`CView`可讓您傳遞的描述文件的哪些組件已修改的資訊。 這項 「 提示 」 機制可讓您限制檢視必須重新繪製的區域。 `OnUpdate` 採用兩個 「 提示 」 引數。 第一個*lHint*，型別的**LPARAM**，可讓您傳遞您要在第二個，任何資料*pHint*，型別的`CObject`*，可讓您將指標傳遞給任何衍生的物件從`CObject`。

無效的檢視時，Windows 會傳送它**WM_PAINT**訊息。 檢視的[OnPaint](../mfc/reference/cwnd-class.md#onpaint)處理常式函式會回應訊息藉由建立類別的裝置內容物件[CPaintDC](../mfc/reference/cpaintdc-class.md) ，並呼叫您的檢視`OnDraw`成員函式。 您通常不必撰寫覆寫`OnPaint`處理常式函式。

A[裝置內容](../mfc/device-contexts.md)是 Windows 資料結構，其中包含的顯示器或印表機等裝置的繪製屬性的相關資訊。 所有的繪製呼叫都會經過裝置內容物件。 在畫面上，繪製`OnDraw`傳遞`CPaintDC`物件。 繪製在印表機上，它會傳遞[CDC](../mfc/reference/cdc-class.md)對目前印表機設定的物件。

您的程式碼檢視中繪製的第一次擷取文件的指標，則會透過裝置內容的繪製呼叫。 以下簡單的`OnDraw`範例說明此程序：

[!code-cpp[NVC_MFCDocView#1](../mfc/codesnippet/cpp/drawing-in-a-view_1.cpp)]

在此範例中，您會定義`GetData`做為衍生的文件類別的成員。

這個範例會列印任何字串，它會從 文件中，在檢視置中取得。 如果`OnDraw`呼叫是針對螢幕繪圖`CDC`傳入的物件*pDC*會`CPaintDC`的建構函式已呼叫`BeginPaint`。 繪圖函式的呼叫都會經過的裝置內容指標。 裝置內容和繪製呼叫的相關資訊，請參閱類別[CDC](../mfc/reference/cdc-class.md)中*MFC 參考 》* 並[使用視窗物件](../mfc/working-with-window-objects.md)。

如需如何撰寫的範例`OnDraw`，請參閱 < [MFC 範例](../overview/visual-cpp-samples.md)。

## <a name="see-also"></a>另請參閱

[使用檢視](../mfc/using-views.md)
