---
title: 'TN040: MFC OLE 就地調整大小和縮放 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.ole
dev_langs:
- C++
helpviewer_keywords:
- resizing in-place
- TN040
- zooming and in-place activation
- in-place activation, zooming and resizing
ms.assetid: 4d7859bd-0b2e-4254-be62-2735cecf02c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bf8b90aed96135967167c8048f775fc7530f85d6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="tn040-mfcole-in-place-resizing-and-zooming"></a>TN040：MFC/OLE 就地調整大小和縮放
> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
 這個提示會討論與就地編輯相關的問題，以及伺服器應該如何完成正確的縮放和就地調整大小。 對於就地啟用，是進一步採取 WYSIWYG 概念，即容器和伺服器會彼此互相合作，並以相同的方式特別說明 OLE 規格。  
  
 由於容器和支援就地啟用的伺服器之間的密切互動，因此從應該維護的使用者會有幾項期待：  
  
-   版面的顯示 (在 `COleServerItem::OnDraw` 覆寫中繪製的中繼檔) 應該與其繪製以供編輯時一模一樣 (除了看不到編輯工具以外)。  
  
-   當容器縮放時，伺服器視窗應該也隨之縮放！  
  
-   容器和伺服器應該使用相同的度量顯示供編輯的物件。 這表示使用的數字為基礎的對應模式*邏輯*每英吋的像素 — 每英吋，轉譯顯示裝置上時不是實體像素為單位。  
  
> [!NOTE]
>  由於就地啟用只套用於內嵌的 (未連結的) 項目，所以縮放只套用於內嵌的物件。 您會在用於縮放的 `COleServerDoc` 和 `COleServerItem` 中看到 API。 這二分法的原因是只有對於連結和內嵌的項目都有效的函式是在 `COleServerItem` (這可讓您擁有一般實作) 中，而只有對於內嵌的物件有效的函式是位於 `COleServerDoc` 類別 (以伺服器的角度，其為內嵌的 `document`) 中。  
  
 大部分負載在伺服器實作上，該伺服器必須知道容器的縮放因數並適當地修改其編輯介面。 但是伺服器如何決定容器使用的縮放因數  
  
## <a name="mfc-support-for-zooming"></a>MFC 支援縮放  
 目前的縮放因數可以透過呼叫 `COleServerDoc::GetZoomFactor` 來決定。 當文件不是就地啟用時呼叫此項，總是會產生 100% 縮放因數 (或 1:1 比例)。 當就地啟用作用中呼叫它，則可能傳回 100% 以外的值。  
  
 如需正確縮放的範例，請參閱 MFC OLE 範例[HIERSVR](../visual-cpp-samples.md)。 HIERSVR 中的縮放伴隨的事實是其顯示文字，而文字一般並不會線性方式 (提示、印刷樣式慣例、設計寬度和高度都讓問題更複雜) 縮放。 然而，HIERSVR 是正確實作縮放的合理參考，因此，MFC 教學課程[SCRIBBLE](../visual-cpp-samples.md) （步驟 7）。  
  
 `COleServerDoc::GetZoomFactor` 是根據可從容器或從實作您的 `COleServerItem` 和 `COleServerDoc` 類別取得的幾個不同度量，來決定縮放因數。 簡言之，目前的縮放因數取決於下列公式：  
  
```  
Position Rectangle (PR) / Container Extent (CE)  
```  
  
 POSITION RECTANGLE 取決於容器。 當呼叫 `COleClientItem::OnGetItemPosition` 時，以及當容器呼叫伺服器的 `COleServerDoc::OnSetItemRects` 時更新的話 (使用呼叫 `COleClientItem::SetItemRects`)，它會在就地啟用期間傳回到伺服器。  
  
 CONTAINER EXTENT 的計算稍微比較複雜。 如果容器已呼叫 `COleServerItem::OnSetExtent` (使用呼叫 `COleClientItem::SetExtent`)，則 CONTAINER EXTENT 是轉換為像素 (以每邏輯英吋的像素數為基礎) 的這個值。 如果容器未呼叫 SetExtent (通常是如此)，則 CONTAINER EXTENT 是從 `COleServerItem::OnGetExtent` 傳回的大小。 因此，如果容器未呼叫 SetExtent，架構會假設，如果容器已經呼叫它和 100%的自然範圍 (從傳回的值**coleserveritem:: Getextent**)。 以另一個方式陳述，架構會假設容器是 100% (不多也不少) 顯示項目。  
  
 要注意的是，雖然 `COleServerItem::OnSetExtent` 和 `COleServerItem::OnGetExtent` 具有類似的名稱，但是它們不操作相同屬性的項目。 呼叫 `OnSetExtent` 是為了讓伺服器知道物件有多少部分會顯示在容器 (不論縮放因數) 中，而容器會呼叫 `OnGetExtent` 決定物件的理想大小。  
  
 查看所牽涉的每個 API，您就可以更清楚了解：  
  
## <a name="coleserveritemongetextent"></a>COleServerItem::OnGetExtent  
 這個函式應項目的 HIMETRIC 單位傳回「原始大小」。 最好的方式將「原始大小」視為會定義其在列印時顯示的大小。 此處傳回的大小是特定項目內容的常數 (很像中繼檔，其為特定項目的常數)。 當縮放套用到項目時，這個大小不會變更。 當容器藉由呼叫 `OnSetExtent` 給予項目或多或少的空間時，它通常不會變更。 變更的範例可能是沒有「邊界」功能的簡單文字編輯器，自動換行是根據容器所傳送的最後一個範圍。 如果伺服器變更，伺服器可能要在系統登錄中設定 OLEMISC_RECOMPOSEONRESIZE 位元 (如需此選項的詳細資訊，請參閱 OLE SDK 文件)。  
  
## <a name="coleserveritemonsetextent"></a>COleServerItem::OnSetExtent  
 當容器「或多或少」顯示物件時，會呼叫這個函式。 大多數容器根本不會呼叫這個方法。 預設實作會以「m_sizeExtent」儲存從容器接收的最後一個值，其如以上所述在運算 CONTAINER EXTENT 值時，會在 `COleServerDoc::GetZoomFactor` 中使用。  
  
## <a name="coleserverdoconsetitemrects"></a>COleServerDoc::OnSetItemRects  
 只有在文件為就地啟用作用中時，呼叫這個函式。 當容器更新項目的位置或套用到項目的裁剪時，便會呼叫它。 如上所述，POSITION RECTANGLE 提供計算縮放因數的列舉程式。 伺服器可能要求呼叫 `COleServerDoc::RequestPositionChange` 來變更項目位置。 容器可能會或可能藉由呼叫無法回應此要求`OnSetItemRects`(藉由呼叫**coleserveritem:: Setitemrects**)。  
  
## <a name="coleserverdocondraw"></a>COleServerDoc::OnDraw  
 必須要了解的是透過 `COleServerItem::OnDraw` 的覆寫所建立的中繼檔，不論目前縮放因數為何，會產生完全相同的中繼檔。 容器會適當地縮放中繼檔。 這是檢視的 `OnDraw` 和伺服器項目的 `OnDraw` 之間的重要區別。 檢視會處理縮放，項目則只會建立*將*中繼檔並讓容器進行適當的縮放。  
  
 如果您的文件是就地啟用的話，確保您的伺服器正常運作的最好方式是使用實作 `COleServerDoc::GetZoomFactor`。  
  
## <a name="mfc-support-for-in-place-resizing"></a>MFC 支援就地調整大小  
 MFC 會如 OLE 2 規格中所述完全實作就地調整介面大小。 使用者介面受到`COleResizeBar`類別，自訂訊息**WM_SIZECHILD**，和此訊息中的特殊處理`COleIPFrameWnd`。  
  
 您可能會想要實作以不同於架構所提供的方式處理此訊息。 如上所述，架構會將就地調整大小的結果留給容器來決定，而伺服器會回應縮放因數中的變更。 如果容器在處理其 `COleClientItem::OnChangeItemPosition` (因為呼叫 `COleServerDoc::RequestPositionChange` 的緣故而呼叫) 期間透過設定 CONTAINER EXTENT 和 POSITION RECTANGLE 二者來反應的話，則就地調整大小會導致在編輯視窗中「或多或少」顯示項目。 如果容器在處理 `COleClientItem::OnChangeItemPosition` 期間只是透過設定 POSITION RECTANGLE 來反應的話，則縮放因數會變更，並且項目會「放大或縮小」顯示。  
  
 伺服器可以控制 (某種程度上) 在此交涉期間會發生什麼情況。 例如，當使用者在就地編輯項目期間調整視窗大小時，試算表可以選擇顯示更多或更少儲存格。 文字處理器可能會選擇變更「頁面邊界」，以便讓它們與視窗相同並將文字重新換行至新邊界。 當調整大小完成時，伺服器會變更原始範圍 (從 `COleServerItem::OnGetExtent` 傳回的大小) 以實作此項。 這會讓 POSITION RECTANGLE 和 CONTAINER EXTENT 以相同的數量進行變更，產生相同的縮放因數，但是檢視區域會較大或者較小。 此外，在 `OnDraw` 所產生的中繼檔中，會或多或少顯示文件。 在此情況下，當使用者調整項目大小，而不只是檢視區域時，文件本身會隨之變更。  
  
 您可以實作自訂調整大小，同時仍然利用提供的使用者介面`COleResizeBar`藉由覆寫**WM_SIZECHILD**訊息中您`COleIPFrameWnd`類別。 如需有關的細節**WM_SIZECHILD**，請參閱[技術提示 24](../mfc/tn024-mfc-defined-messages-and-resources.md)。  
  
## <a name="see-also"></a>另請參閱  
 [依數字的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)

