---
title: 如何： 在您的程式碼中實作追蹤 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CRectTracker class [MFC], implementing trackers
ms.assetid: baaeca2c-5114-485f-bf58-8807db1bc973
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dc21369dd8d241bd00da2a0a8005c977094c3abf
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932090"
---
# <a name="how-to-implement-tracking-in-your-code"></a>如何：在您的程式碼中實作追蹤
若要追蹤 OLE 項目，您必須處理特定項目，例如按一下項目或更新文件檢視相關的事件。 在所有情況下，這就足夠宣告暫存[CRectTracker](../mfc/reference/crecttracker-class.md)物件，並透過此物件來管理項目。  
  
 當使用者選取的項目，或插入的功能表命令的物件時，您必須初始化追蹤程式，以適當的樣式，來代表 OLE 項目的狀態。 下表概述 OCLIENT 範例所使用的慣例。 如需有關這些樣式的詳細資訊，請參閱`CRectTracker`。  
  
### <a name="container-styles-and-states-of-the-ole-item"></a>容器的樣式和的 OLE 項目狀態  
  
|顯示樣式|OLE 項目的狀態|  
|---------------------|-----------------------|  
|點線框|項目連結|  
|實心框線|文件中內嵌項目|  
|調整控點大小|目前選取項目|  
|包含陰影的框線|項目是目前就地啟用作用中|  
|影線圖樣覆疊項目|項目的伺服器已開啟|  
  
 您可以處理這類初始化容易使用的程序會檢查 OLE 項目狀態，並設定適當的樣式。 `SetupTracker`函式位於 OCLIENT 範例示範追蹤器初始化。 此函式的參數是追蹤程式，位址*pTracker*; 與追蹤程式，用戶端項目的指標*pItem*; 以及矩形的指標*pTrueRect*. 此函式的更完整的範例，請參閱 MFC OLE 範例[OCLIENT](../visual-cpp-samples.md)。  
  
 **SetupTracker**程式碼範例會顯示在單一函式，函式的線條會穿插討論函式的功能：  
  
 [!code-cpp[NVC_MFCOClient#1](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_1.cpp)]  
  
 追蹤程式會初始化所設定的最小大小及清除的追蹤器樣式。  
  
 [!code-cpp[NVC_MFCOClient#2](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_2.cpp)]  
  
 下列幾行，請檢查目前是否已選取項目和項目連結至文件是否內嵌在其中。 調整大小控點位於內部的框線會加入至樣式，表示目前已選取項目。 如果項目連結到您的文件，則會使用虛線的框線樣式。 如果內嵌的項目，會使用實心框線。  
  
 [!code-cpp[NVC_MFCOClient#3](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_3.cpp)]  
  
 下列程式碼覆疊開啟影線圖樣如果項目目前的項目。  
  
 [!code-cpp[NVC_MFCOClient#4](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_4.cpp)]  
  
 追蹤程式顯示上時，您就可以呼叫此函式。 例如，呼叫此函式從`OnDraw`檢視類別函式。 檢視重繪時，這會更新追蹤程式的外觀。 如需完整範例，請參閱`CMainView::OnDraw`函式的 MFC OLE 範例[OCLIENT](../visual-cpp-samples.md)。  
  
 在您的應用程式需要追蹤程式的程式碼，例如調整大小、 移動或叫用偵測的事件會發生。 這些動作通常會指出，正在嘗試抓取或移動項目。 在這些情況下，您必須決定控制點： 調整大小控點或部分之間的框線上調整大小控點。 `OnLButtonDown`訊息處理常式會測試相對於項目的滑鼠位置的好地方。 呼叫以`CRectTracker::HitTest`。 如果測試傳回以外的值`CRectTracker::hitOutside`、 項目會被調整大小或移動。 因此，您應該進行的呼叫`Track`成員函式。 請參閱`CMainView::OnLButtonDown`函式位於 MFC OLE 範例[OCLIENT](../visual-cpp-samples.md)完成完整的範例。  
  
 `CRectTracker`類別會提供用來指出是否移動、 調整大小，或拖曳操作正在進行中的數個不同的資料指標圖形。 若要處理此事件，檢查是否已選取目前下滑鼠的項目。 如果是，呼叫以`CRectTracker::SetCursor`，或呼叫的預設處理常式。 下列範例取自 MFC OLE 範例[OCLIENT](../visual-cpp-samples.md):  
  
 [!code-cpp[NVC_MFCOClient#5](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_5.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [追蹤器：在 OLE 應用程式中實作追蹤器](../mfc/trackers-implementing-trackers-in-your-ole-application.md)

