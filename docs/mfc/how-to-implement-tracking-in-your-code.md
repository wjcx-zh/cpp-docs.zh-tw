---
title: 如何：在您的程式碼中實作追蹤
ms.date: 11/04/2016
helpviewer_keywords:
- CRectTracker class [MFC], implementing trackers
ms.assetid: baaeca2c-5114-485f-bf58-8807db1bc973
ms.openlocfilehash: 3d71543261021c7e20041d317401b7b7b8d0616e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621661"
---
# <a name="how-to-implement-tracking-in-your-code"></a>如何：在您的程式碼中實作追蹤

若要追蹤 OLE 專案，您必須處理與專案相關的特定事件，例如按一下專案或更新檔的視圖。 在所有情況下，宣告暫存[CRectTracker](reference/crecttracker-class.md)物件，並透過這個物件操作專案就已足夠。

當使用者選取專案或使用功能表命令插入物件時，您必須使用適當的樣式來初始化追蹤程式，以代表 OLE 專案的狀態。 下表概述 OCLIENT 範例所使用的慣例。 如需這些樣式的詳細資訊，請參閱 `CRectTracker` 。

### <a name="container-styles-and-states-of-the-ole-item"></a>OLE 專案的容器樣式和狀態

|顯示的樣式|OLE 專案的狀態|
|---------------------|-----------------------|
|點框線|專案已連結|
|實心框線|專案內嵌在您的檔中|
|調整控點大小|目前已選取專案|
|影線框線|專案目前為使用中狀態|
|影線圖樣重迭專案|專案的伺服器已開啟|

您可以使用檢查 OLE 專案狀態的程式，並設定適當的樣式，輕鬆地處理此初始化。 在 `SetupTracker` OCLIENT 範例中找到的函式會示範追蹤程式初始化。 此函式的參數是追蹤程式的位址， *pTracker*;與追蹤程式相關的用戶端專案指標， *pItem*;以及指向矩形的指標*pTrueRect*。 如需此函式的更完整範例，請參閱 MFC OLE 範例[OCLIENT](../overview/visual-cpp-samples.md)。

**SetupTracker**程式碼範例呈現單一函式;函式的各行與函式功能的討論交錯：

[!code-cpp[NVC_MFCOClient#1](codesnippet/cpp/how-to-implement-tracking-in-your-code_1.cpp)]

追蹤器的初始化方式是設定最小大小，並清除追蹤器的樣式。

[!code-cpp[NVC_MFCOClient#2](codesnippet/cpp/how-to-implement-tracking-in-your-code_2.cpp)]

下列幾行會檢查是否目前已選取專案，以及專案是否連結至檔或內嵌于其中。 在框線內的調整大小控點會加入至樣式，表示目前已選取該專案。 如果專案已連結至您的檔，則會使用虛線框線樣式。 如果專案是內嵌的，則會使用實心框線。

[!code-cpp[NVC_MFCOClient#3](codesnippet/cpp/how-to-implement-tracking-in-your-code_3.cpp)]

如果專案目前已開啟，下列程式碼會以影線圖樣來覆迭專案。

[!code-cpp[NVC_MFCOClient#4](codesnippet/cpp/how-to-implement-tracking-in-your-code_4.cpp)]

當追蹤程式必須顯示時，您就可以呼叫此函式。 例如，從 view 類別的函式呼叫這個函式 `OnDraw` 。 這會在重新繪製視圖時，更新追蹤器的外觀。 如需完整範例，請參閱 `CMainView::OnDraw` MFC OLE 範例[OCLIENT](../overview/visual-cpp-samples.md)的功能。

在您的應用程式中，將會發生需要追蹤程式碼的事件，例如調整大小、移動或點擊偵測。 這些動作通常表示嘗試抓取或移動專案。 在這些情況下，您必須決定要抓取的內容：調整大小控點或調整大小控點之間框線的一部分。 `OnLButtonDown`訊息處理常式是測試滑鼠相對於專案之位置的理想位置。 進行呼叫 `CRectTracker::HitTest` 。 如果測試傳回其他 `CRectTracker::hitOutside` 專案，則會調整大小或移動專案。 因此，您應該對成員函式進行呼叫 `Track` 。 如需 `CMainView::OnLButtonDown` 完整範例，請參閱 MFC OLE [sample OCLIENT](../overview/visual-cpp-samples.md)中的函數。

`CRectTracker`類別提供數種不同的游標圖形，用來指出移動、調整大小或拖曳作業是否正在進行中。 若要處理此事件，請檢查是否已選取目前在滑鼠底下的專案。 如果是，請呼叫 `CRectTracker::SetCursor` ，或呼叫預設處理常式。 下列範例來自 MFC OLE 範例[OCLIENT](../overview/visual-cpp-samples.md)：

[!code-cpp[NVC_MFCOClient#5](codesnippet/cpp/how-to-implement-tracking-in-your-code_5.cpp)]

## <a name="see-also"></a>另請參閱

[追蹤器：在 OLE 應用程式中實作追蹤器](trackers-implementing-trackers-in-your-ole-application.md)
