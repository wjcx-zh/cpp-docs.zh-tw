---
title: HOW TO：在您的程式碼中實作追蹤
ms.date: 11/04/2016
helpviewer_keywords:
- CRectTracker class [MFC], implementing trackers
ms.assetid: baaeca2c-5114-485f-bf58-8807db1bc973
ms.openlocfilehash: af8e1b72bde268a15012515065853daa617936e4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57283978"
---
# <a name="how-to-implement-tracking-in-your-code"></a>HOW TO：在您的程式碼中實作追蹤

若要追蹤 OLE 項目，您必須處理相關的項目，例如按一下項目或更新文件檢視特定事件。 在所有情況下，就足以宣告暫存[CRectTracker](../mfc/reference/crecttracker-class.md)物件，並管理透過此物件的項目。

當使用者選取的項目，或插入具有功能表命令的物件時，您必須初始化以適當的樣式，來表示 OLE 項目的狀態追蹤程式。 下表概述 OCLIENT 範例所使用的慣例。 如需有關這些樣式的詳細資訊，請參閱`CRectTracker`。

### <a name="container-styles-and-states-of-the-ole-item"></a>容器的樣式和 OLE 項目的狀態

|顯示的樣式|OLE 項目的狀態|
|---------------------|-----------------------|
|虛線的框線|項目連結|
|實線框線|項目內嵌在您的文件|
|調整控點大小|目前選取項目|
|陰影的框線|項目是目前就地啟用作用中|
|影線圖樣重疊項目|項目的伺服器已開啟|

您可以處理這項初始化輕鬆使用的程序會檢查 OLE 項目的狀態，並設定適當的樣式。 `SetupTracker` OCLIENT 範例中找到的函式示範追蹤器初始化。 此函式的參數是追蹤程式，地址*pTracker*; 的追蹤程式，與用戶端項目指標*pItem*; 和矩形，指向*pTrueRect*. 此函式的更完整範例，請參閱 MFC OLE 範例[OCLIENT](../visual-cpp-samples.md)。

**SetupTracker**程式碼範例會提供單一函式; 函式的線條會穿插討論函式的功能：

[!code-cpp[NVC_MFCOClient#1](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_1.cpp)]

追蹤器會初始化所設定的最小及清除追蹤器的樣式。

[!code-cpp[NVC_MFCOClient#2](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_2.cpp)]

若要查看目前是否已選取項目和連結至文件或內嵌在其中的項目是否檢查下列幾行。 上框線內側的調整大小控點會加入至樣式，表示目前未選取項目。 如果項目連結到您的文件，則會使用虛線的框線樣式。 如果內嵌的項目，則會使用實線框線。

[!code-cpp[NVC_MFCOClient#3](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_3.cpp)]

下列程式碼覆疊影線圖樣如果項目目前的項目開啟。

[!code-cpp[NVC_MFCOClient#4](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_4.cpp)]

每當有要顯示的追蹤程式，您就可以呼叫此函式。 例如，呼叫這個函式從`OnDraw`檢視類別函式。 檢視會重新繪製時，這會更新追蹤程式的外觀。 如需完整範例，請參閱 <<c0> `CMainView::OnDraw` 函式的 MFC OLE 範例[OCLIENT](../visual-cpp-samples.md)。

在您的應用程式需要追蹤程式的程式碼，例如調整大小、 移動或點擊偵測的事件會發生。 這些動作通常表示有人嘗試抓取或移動項目。 在這些情況下，您需要決定控制點： 調整大小控點或框線之間的部分調整大小控點。 `OnLButtonDown`訊息處理常式會測試與項目相關的滑鼠位置的好地方。 呼叫以`CRectTracker::HitTest`。 如果測試傳回以外的值`CRectTracker::hitOutside`、 項目是因為重新調整大小或移動。 因此，您應該進行的呼叫`Track`成員函式。 請參閱`CMainView::OnLButtonDown`函式位於 MFC OLE 範例[OCLIENT](../visual-cpp-samples.md)如需完整範例。

`CRectTracker`類別提供用來指出是否移動、 調整大小，或拖曳作業正在進行的數個不同的資料指標圖形。 若要處理這個事件，請查看目前在滑鼠的項目是否已選取。 如果是，呼叫以`CRectTracker::SetCursor`，或呼叫預設處理常式。 下列範例是從 MFC OLE 範例[OCLIENT](../visual-cpp-samples.md):

[!code-cpp[NVC_MFCOClient#5](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_5.cpp)]

## <a name="see-also"></a>另請參閱

[追蹤器：在 OLE 應用程式中實作追蹤器](../mfc/trackers-implementing-trackers-in-your-ole-application.md)
