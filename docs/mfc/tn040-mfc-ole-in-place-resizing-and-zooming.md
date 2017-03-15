---
title: "TN040：MFC/OLE 就地調整大小和縮放 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "就地啟用, 縮放和調整大小"
  - "就地調整大小"
  - "TN040"
  - "縮放和就地啟用"
ms.assetid: 4d7859bd-0b2e-4254-be62-2735cecf02c6
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN040：MFC/OLE 就地調整大小和縮放
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。  因此，有些程序和主題可能已過期或不正確。  如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
 這個標記會討論問題與就地編輯相關，而且伺服器應該如何完成正確縮放和就地調整大小。  就地啟動， WYSIWYG 概念採取進一步的因為容器和伺服器互相共同作業和在方式特別說明這個 OLE 規格。  
  
 由於支援其中就地啟動的容器和伺服器之間的關閉互動都是從應該維護的使用者的預期:  
  
-   介紹顯示 \(在 `COleServerItem::OnDraw` 覆寫繪製的中繼檔\) 應該看到相同，以便進行編輯時， \(除了編輯工具繪製不可見\)。  
  
-   當容器縮放時，伺服器視窗也是應該\!  
  
-   使用相同的度量，容器和伺服器應該顯示編輯的物件。  這表示使用根據  *邏輯*  每英吋像素 \(PPI\) —不實體 \(單位為每英吋的像素數目的對應方式，樣式，當呈現顯示裝置上時。  
  
> [!NOTE]
>  由於就地啟動只適用於內嵌的項目 \(未連結\)，縮放只適用於內嵌物件。  為縮放使用會查看兩個 API 的 `COleServerDoc` 和 `COleServerItem` 。  這二分法原因是連結與內嵌項目有效的函式進行內嵌物件是有效的 `COleServerItem` \(這可讓您設定通用實作\) 和函式位於 `COleServerDoc` 類別 \(來自伺服器的方面，內嵌\) 的則為 `document` 。  
  
 大部分負載在伺服器實作上，因為伺服器必須知道容器的縮放因數和修改其編輯介面屬性。  但是，伺服器決定縮放因數容器使用?  
  
## MFC 支援縮放  
 目前的縮放因數可以取決於呼叫 `COleServerDoc::GetZoomFactor`。  呼叫這個方法，在文件不是就地啟動一定會產生 100% 縮放因數 1:1 \(或比\)。  呼叫它 100% 以外的設定時，，當就地使用中可能傳回值。  
  
 如需正確縮放範例請參閱 MFC OLE [HIERSVR](../top/visual-cpp-samples.md)範例。  放大 HIERSVR 由這個事實所顯示的文字和文字變得很複雜，不線形一般而言，名稱 \(提示、印刷樣式慣例、設計寬度和高度都讓問題更複雜\)。  但是， HIERSVR 是實作的正確縮放音效參考，和，因此是 MFC 教學課程 [Scribble](../top/visual-cpp-samples.md) \(步驟 7\)。  
  
 `COleServerDoc::GetZoomFactor` 判斷以一些不同的度量可取得的縮放因數從容器或從您的 `COleServerItem` 和 `COleServerDoc` 類別的實作。  為了簡化，下列公式取決於目前縮放因數:  
  
```  
Position Rectangle (PR) / Container Extent (CE)  
```  
  
 容器取決於位置矩形。  它會傳回到伺服器在就地啟動時，在呼叫 `COleClientItem::OnGetItemPosition` 時並更新，當容器呼叫伺服器的 `COleServerDoc::OnSetItemRects` \(與 `COleClientItem::SetItemRects`的呼叫\)。  
  
 容器範圍是稍微複雜的計算。  如果容器呼叫 `COleServerItem::OnSetExtent` \(與 `COleClientItem::SetExtent`的呼叫\)，則容器範圍為這個值會轉換為根據的像素數目的像素每邏輯英吋。  如果容器未呼叫通常是如此\) 的 SetExtent \(，則容器範圍是從 `COleServerItem::OnGetExtent`所傳回的大小。  因此，容器，如果未呼叫 SetExtent，架構，並假設，如果它做容器將呼叫它與 100% 自然範圍 \(從 **COleServerItem::GetExtent**所傳回的值\)。  陳述式的另一個方式，架構會假設，容器顯示 100% \(沒有，沒有\) 項目。  
  
 很重要的，不過， `COleServerItem::OnSetExtent` 和 `COleServerItem::OnGetExtent` 具有相同的名稱，但是操作項目相同的屬性。  `OnSetExtent` 呼叫告知伺服器多少物件會顯示在容器 \(不論縮放因數\)，而且 `OnGetExtent` 是由容器呼叫來判斷物件的理想的大小。  
  
 藉由查看所包含之每個應用程式開發介面，您可以取得更清楚的圖片:  
  
## COleServerItem::OnGetExtent  
 這個函式應傳回原始大小」項目的 HIMETRIC 單位。  最好的方式視為自然大小會定義它，因為它的大小，可能會出現在列印。  傳回的大小此處為特定項目內容是常數 \(很像中繼檔，為特定項目是常數\)。  當縮放套用到項目時，這個大小不會變更。  它通常不會變更，當容器藉由呼叫 `OnSetExtent`重新命名項目較多或較少空間。  變更的範例是簡單的文字編輯器沒有包裝根據最後一個範圍的文字傳送由容器的邊界」功能。  如果伺服器變更，伺服器可能要設定在系統登錄的 OLEMISC\_RECOMPOSEONRESIZE 位元 \(請參閱 OLE SDK 文件有關此選項的詳細資訊\)。  
  
## COleServerItem::OnSetExtent  
 當容器顯示「或多或少」物件時，呼叫這個函式。  多數容器根本不會呼叫這個方法。  預設實作「m\_sizeExtent」儲存從容器接收的最後一個值，用於 `COleServerDoc::GetZoomFactor` ，在計算中描述的容器範圍值上方時。  
  
## COleServerDoc::OnSetItemRects  
 只有在文件是就地啟動時，這個函式呼叫。  當容器更新任何項目的位置或裁剪套用到項目時，會呼叫。  位置矩形，如先前所述，為縮放因數計算的分子。  伺服器可能要求呼叫 `COleServerDoc::RequestPositionChange`變更項目的位置。  容器可以或不可以回答要求透過呼叫 `OnSetItemRects` \(與 **COleServerItem::SetItemRects**的呼叫\)。  
  
## COleServerDoc::OnDraw  
 注意覆寫建立的中繼檔 `COleServerItem::OnDraw` 是重要的產生相同的中繼檔，不論目前縮放因數，。  容器會縮放中繼檔屬性。  這是檢視的 `OnDraw` 和伺服器項目的 `OnDraw`的重要區別。  這個檢視處理縮放，項目建立 *zoomable* 中繼檔和讓容器決定進行適當縮放。  
  
 最好的方式可確保您的伺服器正常運作時要使用的 `COleServerDoc::GetZoomFactor` 實作，如果您的資料是就地啟動。  
  
## MFC 支援就地調整大小  
 MFC 完全實作就地調整大小的介面如 OLE 2 規格中所述。  這個使用者介面是由 `COleResizeBar` 類別、自訂訊息 **WM\_SIZECHILD**和此訊息特殊處理在 `COleIPFrameWnd`的支援。  
  
 您可以實作此訊息的其他處理比架構所提供。  如上所述，架構會留下就地調整大小的結果則由容器決定—伺服器回應在縮放因數的變更。  如果容器將反應容器範圍和位置矩形在處理其 `COleClientItem::OnChangeItemPosition` \(因為呼叫 `COleServerDoc::RequestPositionChange`\) 然後就地調整造成顯示「或多或少」項目在編輯視窗中。  在處理 `COleClientItem::OnChangeItemPosition`，如果容器藉由設定位置矩形反應，縮放因數會變更，而且項目顯示「或」放大。  
  
 伺服器可以控制 \(對某種程度\) 以及這個項目時發生。  報告，例如可能決定顯示更多或更少的儲存格，當使用者調整視窗大小時，就地編輯中的項目。  文字處理器可能會決定將「頁面邊界」，讓它們與視窗和 rewrap 文字至新框線。  伺服器進行變更自然範圍實作此 \(從 `COleServerItem::OnGetExtent`傳回的大小\)，當調整完成時。  這會讓矩形位置和容器範圍由相同數量的變更，會造成相同縮放因數，不過，一個更大或更小的檢視區域。  此外，以上或少文件會顯示在 `OnDraw`所產生的中繼檔。  在這種情況下，文件已變更，當使用者調整項目，而不是檢視區域。  
  
 您可以實作自訂調整大小和仍然支援 `COleResizeBar` 提供的使用者介面傳遞中覆寫 `COleIPFrameWnd` 類別 **WM\_SIZECHILD** 的訊息。  如需 **WM\_SIZECHILD**的詳細資訊，請參閱 [Technical Note 24](../mfc/tn024-mfc-defined-messages-and-resources.md)。  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)