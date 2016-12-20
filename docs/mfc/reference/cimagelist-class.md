---
title: "CImageList Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CImageList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CImageList class"
  - "image lists [C++], CImageList class"
  - "Windows common controls [C++], CImageList"
ms.assetid: b6d1a704-1c82-4548-8a8f-77972adc98a5
caps.latest.revision: 19
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CImageList Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供 Windows 通用影像清單控制項的功能。  
  
## 語法  
  
```  
class CImageList : public CObject  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CImageList::CImageList](../Topic/CImageList::CImageList.md)|建構 `CImageList` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CImageList::Add](../Topic/CImageList::Add.md)|將影像或影像加入至影像清單。|  
|[CImageList::Attach](../Topic/CImageList::Attach.md)|附加至 `CImageList` 影像清單物件。|  
|[CImageList::BeginDrag](../Topic/CImageList::BeginDrag.md)|將影像的開始。|  
|[CImageList::Copy](../Topic/CImageList::Copy.md)|複製到 `CImageList` 物件內的影像。|  
|[CImageList::Create](../Topic/CImageList::Create.md)|使用影像清單並將其附加至 `CImageList` 物件。|  
|[CImageList::DeleteImageList](../Topic/CImageList::DeleteImageList.md)|刪除影像清單。|  
|[CImageList::DeleteTempMap](../Topic/CImageList::DeleteTempMap.md)|呼叫 [CWinApp](../../mfc/reference/cwinapp-class.md) 閒置時間管理員刪除所有暫存 `CImageList` 物件由 `FromHandle`建立。|  
|[CImageList::Detach](../Topic/CImageList::Detach.md)|中斷連結 `CImageList` 物件建立影像清單物件並將控制代碼傳回至影像清單的。|  
|[CImageList::DragEnter](../Topic/CImageList::DragEnter.md)|在拖曳作業和顯示期間的封鎖更新拖曳影像在指定的位置。|  
|[CImageList::DragLeave](../Topic/CImageList::DragLeave.md)|開啟視窗並隱藏拖曳影像，使視窗進行更新。|  
|[CImageList::DragMove](../Topic/CImageList::DragMove.md)|移動在拖放作業期間被拖曳的影像。|  
|[CImageList::DragShowNolock](../Topic/CImageList::DragShowNolock.md)|顯示或隱藏拖曳影像在拖曳作業期間，不會鎖定視窗。|  
|[CImageList::Draw](../Topic/CImageList::Draw.md)|繪製在拖放作業期間被拖曳的影像。|  
|[CImageList::DrawEx](../Topic/CImageList::DrawEx.md)|以指定之裝置內容中繪製影像清單項目。  函式會使用指定的繪製樣式並以指定的色彩混用的影像。|  
|[CImageList::DrawIndirect](../Topic/CImageList::DrawIndirect.md)|從影像清單中繪製影像。|  
|[CImageList::EndDrag](../Topic/CImageList::EndDrag.md)|結束拖曳作業。|  
|[CImageList::ExtractIcon](../Topic/CImageList::ExtractIcon.md)|若要根據影像和遮罩的圖示會出現在影像清單。|  
|[CImageList::FromHandle](../Topic/CImageList::FromHandle.md)|傳回指向 `CImageList` 物件，將控制代碼影像清單。  如果有 `CImageList` 物件與任何控制代碼，暫存 `CImageList` 物件建立和附加。|  
|[CImageList::FromHandlePermanent](../Topic/CImageList::FromHandlePermanent.md)|傳回指向 `CImageList` 物件，將控制代碼影像清單。  如果有 `CImageList` 物件與任何控制代碼， **NULL** 傳回。|  
|[CImageList::GetBkColor](../Topic/CImageList::GetBkColor.md)|擷取影像清單中目前的背景色彩。|  
|[CImageList::GetDragImage](../Topic/CImageList::GetDragImage.md)|取得將使用的暫存影像清單。|  
|[CImageList::GetImageCount](../Topic/CImageList::GetImageCount.md)|擷取影像數目影像清單的。|  
|[CImageList::GetImageInfo](../Topic/CImageList::GetImageInfo.md)|擷取的相關資訊。|  
|[CImageList::GetSafeHandle](../Topic/CImageList::GetSafeHandle.md)|擷取 **m\_hImageList**。|  
|[CImageList::Read](../Topic/CImageList::Read.md)|讀取檔案的一個影像清單的。|  
|[CImageList::Remove](../Topic/CImageList::Remove.md)|從影像清單中移除影像。|  
|[CImageList::Replace](../Topic/CImageList::Replace.md)|將新的影像取代影像清單中的影像。|  
|[CImageList::SetBkColor](../Topic/CImageList::SetBkColor.md)|設定影像清單的背景色彩。|  
|[CImageList::SetDragCursorImage](../Topic/CImageList::SetDragCursorImage.md)|建立新的拖曳影像。|  
|[CImageList::SetImageCount](../Topic/CImageList::SetImageCount.md)|重設計數在影像清單中的影像。|  
|[CImageList::SetOverlayImage](../Topic/CImageList::SetOverlayImage.md)|將影像的以零起始的索引會覆疊遮罩要用的影像清單。|  
|[CImageList::Write](../Topic/CImageList::Write.md)|將檔案寫入一個影像清單的。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CImageList::operator HIMAGELIST](../Topic/CImageList::operator%20HIMAGELIST.md)|傳回 `HIMAGELIST` 附加至 `CImageList`。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CImageList::m\_hImageList](../Topic/CImageList::m_hImageList.md)|包含影像清單的控制代碼已附加至這個物件。|  
  
## 備註  
 「影像清單」相同大小的影像集，每一個都可以由其以零起始的索引參考。  影像清單是用來有效管理一組大型圖示或點陣圖。  在影像清單中的所有影像在螢幕裝置格式的單一，寬點陣圖包含。  影像清單也可以包括包含遮罩用來以透明方式繪製影像的單色點陣圖 \(圖示樣式\)。  Microsoft Win32 應用程式發展介面 \(API\) \(API\) 提供影像繪製影像，可讓您建立和終結影像清單，並加入和移除影像，取代影像，合併影像清單函式和影像拖曳。  
  
 這個控制項 \(也 `CImageList` 類別\) 給在 Windows 95 \/98 和 Windows NT 3.51 版之下的程式才能使用 \(含\) 以後版本。  
  
 如需使用 `CImageList`的資訊，請參閱 [控制項](../../mfc/controls-mfc.md) 和 [使用 CImageList](../../mfc/using-cimagelist.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CImageList`  
  
## 需求  
 **Header:** afxcmn.h  
  
## 請參閱  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CListCtrl Class](../../mfc/reference/clistctrl-class.md)   
 [CTabCtrl Class](../../mfc/reference/ctabctrl-class.md)