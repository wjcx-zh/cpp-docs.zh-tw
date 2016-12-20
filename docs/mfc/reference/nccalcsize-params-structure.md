---
title: "NCCALCSIZE_PARAMS 結構 | Microsoft Docs"
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
  - "NCCALCSIZE_PARAMS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "NCCALCSIZE_PARAMS 結構"
ms.assetid: 3424cd9f-806a-4089-82fb-414187589edf
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# NCCALCSIZE_PARAMS 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

 `NCCALCSIZE_PARAMS` 結構包含的應用程式可以使用在處理資訊 `WM_NCCALCSIZE` 計算大小、 位置及有效的用戶端區域內容視窗的訊息。  
  
## <a name="syntax"></a>語法  
  
```  
 
    typedef struct tagNCCALCSIZE_PARAMS {  
    RECT rgrc[3];  
    PWINDOWPOS lppos;  
} NCCALCSIZE_PARAMS;  
```  
  
#### <a name="parameters"></a>參數  
 *rgrc*  
 指定矩形的陣列。 第一個包含新的座標，移動或調整大小的視窗。 移動或調整大小之前，第二個包含視窗的座標。 移動或調整大小之前，第三個包含視窗的用戶端區域的座標。 如果該視窗的子視窗，座標是相對於父視窗的用戶端區域。 如果視窗是最上層視窗，座標是相對於螢幕。  
  
 *lppos*  
 指向 [WINDOWPOS](../../mfc/reference/windowpos-structure1.md) 結構，其中包含造成無法移動或調整視窗的作業中指定的大小和位置值。  
  
## <a name="requirements"></a>需求  
 **標頭︰** winuser.h.  
  
## <a name="see-also"></a>請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnNcCalcSize](../../mfc/reference/cwnd-class.md#OnNcCalcSize)

