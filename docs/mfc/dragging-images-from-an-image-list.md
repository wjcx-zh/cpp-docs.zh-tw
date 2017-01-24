---
title: "從影像清單拖曳影像 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CImageList 類別, 拖曳影像來源"
  - "從影像清單拖曳影像"
  - "影像清單 [C++], 拖曳影像來源"
  - "影像 [C++], 從影像清單拖曳"
ms.assetid: af691db8-e4f0-4046-b7b9-9acc68d3713d
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 從影像清單拖曳影像
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[CImageList](../mfc/reference/cimagelist-class.md) 包含在螢幕上拖曳影像的函式。  拖曳函式平滑地，色彩正確，而且沒有游標的任何閃爍地移動影像。  遮罩影像或未遮罩影像都可以拖曳。  
  
 [BeginDrag](../Topic/CImageList::BeginDrag.md) 成員函式開始拖曳作業。  參數包含要拖曳的影像的索引和在影像中作用點的位置。  作用點是拖曳函式辨認為影像的實際螢幕位置的單一像素。  一般而言，應用程式設定作用點，以便與滑鼠游標的作用點相符。  [DragMove](../Topic/CImageList::DragMove.md) 成員函式將影像移至新的位置。  
  
 [DragEnter](../Topic/CImageList::DragEnter.md) 成員函式設定在視窗內的拖曳影像的初始位置並繪製影像的位置。  參數包含要繪製影像的視窗的指標以及指定視窗之內的初始位置座標的點。  座標和視窗工作區左上角位置相對，而非客戶端區域。  這也適用於任何影像拖曳函式做為協調做為參數。  這表示您必須補償視窗項目的寬度，例如框線、標題列和功能表列，當指定座標時。  當呼叫 `DragEnter`時，如果您指定 **NULL** 視窗控制代碼，拖曳函式在與桌面視窗相關的裝置內容繪製影像，而且座標是相對於螢幕左上角。  
  
 `DragEnter` 於特定視窗在拖曳作業期間鎖定其他更新。  如果您需要在拖曳作業期間進行繪圖，例如反白顯示拖放作業的目標，您可以使用 [DragLeave](../Topic/CImageList::DragLeave.md) 成員函式，您可以暫時隱藏被拖曳的影像。  您也可以使用 [DragShowNoLock](../Topic/CImageList::DragShowNolock.md) 成員函式。  
  
 在完成拖曳影像時，呼叫 [EndDrag](../Topic/CImageList::EndDrag.md) 。  
  
 [SetDragCursorImage](../Topic/CImageList::SetDragCursorImage.md) 成員函式以合併指定影像 \(通常是滑鼠游標影像\) 與目前拖曳影像建立新的拖曳影像。  由於拖曳函式在拖曳作業期間使用新的影像，您應該使用 Windows [ShowCursor](http://msdn.microsoft.com/library/windows/desktop/ms648396) 函式以在呼叫 `SetDragCursorImage`之後隱藏實際滑鼠游標。  否則，系統可能會在拖曳作業期間出現兩個滑鼠游標。  
  
 當應用程式呼叫 `BeginDrag`時，系統會建立暫存，內部影像清單和複製指定的影像拖曳至內部清單。  使用 [GetDragImage](../Topic/CImageList::GetDragImage.md) 成員函式，擷取指標到暫存拖曳影像清單。  函式也會擷取目前拖曳位置與拖曳影像的位移相對於拖曳位置。  
  
## 請參閱  
 [使用 CImageList](../mfc/using-cimagelist.md)   
 [控制項](../mfc/controls-mfc.md)