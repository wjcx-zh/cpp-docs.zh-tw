---
title: 在檢視中繪圖 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bc716800c35aa922f7912f586d6e5b8429593615
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="drawing-in-a-view"></a>在檢視中繪圖
在您的應用程式中的幾乎所有繪製在檢視中，就會發生`OnDraw`成員函式，您必須在您的檢視類別中覆寫。 (例外狀況是滑鼠繪製、 述[解譯使用者輸入透過檢視](../mfc/interpreting-user-input-through-a-view.md)。)您`OnDraw`覆寫：  
  
1.  藉由呼叫成員函式，您提供的文件取得資料。  
  
2.  藉由呼叫成員函式的架構會將傳遞至裝置內容物件會顯示資料`OnDraw`。  
  
 當文件的資料變更以某種方式時，則必須重新繪製的檢視以反映變更。 通常，這是使用者透過檢視文件上的變更時。 在此情況下，檢視會呼叫文件的[UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews)成員函式以通知所有檢視自行更新相同的文件。 `UpdateAllViews` 呼叫每個檢視[OnUpdate](../mfc/reference/cview-class.md#onupdate)成員函式。 預設實作`OnUpdate`使檢視的整個工作區失效。 您可以覆寫它使只有這些區域的工作區對應至文件已修改的部分。  
  
 `UpdateAllViews`類別成員函式**CDocument**和`OnUpdate`類別成員函式`CView`可讓您傳遞資訊，以描述已修改文件的哪些部分。 這項 「 提示 」 機制可讓您限制檢視必須重繪的區域。 `OnUpdate` 會採用兩個 「 提示 」 引數。 第一個`lHint`，型別**LPARAM**，可讓您傳遞您喜歡，第二個，任何資料`pHint`，型別`CObject`*，可讓您將指標傳遞至任何物件衍生自`CObject`。  
  
 當檢視變成無效時，Windows 將它傳送`WM_PAINT`訊息。 檢視的[OnPaint](../mfc/reference/cwnd-class.md#onpaint)處理常式函式會回應訊息藉由建立類別的裝置內容物件[CPaintDC](../mfc/reference/cpaintdc-class.md) ，呼叫您的檢視`OnDraw`成員函式。 您通常不必撰寫覆寫`OnPaint`處理常式函式。  
  
 A[裝置內容](../mfc/device-contexts.md)是一種 Windows 資料結構，其中包含顯示或印表機等裝置的繪圖屬性相關資訊。 所有的繪製呼叫是透過裝置內容物件。 在畫面上，繪製`OnDraw`傳遞`CPaintDC`物件。 用於繪製在印表機上，它會傳遞[CDC](../mfc/reference/cdc-class.md)印表機設定的物件。  
  
 您的程式碼檢視中繪製的第一次擷取文件的指標，則會透過裝置內容的繪製呼叫。 以下簡單`OnDraw`範例說明此程序：  
  
 [!code-cpp[NVC_MFCDocView#1](../mfc/codesnippet/cpp/drawing-in-a-view_1.cpp)]  
  
 在此範例中，您會定義`GetData`做為您衍生的文件類別的成員。  
  
 這個範例會列印任何字串，它會取得文件，在檢視置中。 如果`OnDraw`呼叫是供螢幕繪圖`CDC`物件傳入`pDC`是`CPaintDC`已經呼叫其建構函式，具有`BeginPaint`。 繪圖函式的呼叫是透過裝置內容的指標。 裝置內容和繪製呼叫的相關資訊，請參閱類別[CDC](../mfc/reference/cdc-class.md)中*MFC 參考*和[使用視窗物件](../mfc/working-with-window-objects.md)。  
  
 如需如何撰寫的範例`OnDraw`，請參閱[MFC 範例](../visual-cpp-samples.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用檢視](../mfc/using-views.md)

