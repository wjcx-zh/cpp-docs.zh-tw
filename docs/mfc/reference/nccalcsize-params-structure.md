---
title: NCCALCSIZE_PARAMS 結構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- NCCALCSIZE_PARAMS
dev_langs:
- C++
helpviewer_keywords:
- NCCALCSIZE_PARAMS structure [MFC]
ms.assetid: 3424cd9f-806a-4089-82fb-414187589edf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 07db612cb6dbde0dd762cf709ac6040bbd836c4b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="nccalcsizeparams-structure"></a>NCCALCSIZE_PARAMS 結構
`NCCALCSIZE_PARAMS`結構包含的應用程式可以使用時處理資訊`WM_NCCALCSIZE`計算大小、 位置和視窗的工作區的有效內容的訊息。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct tagNCCALCSIZE_PARAMS {  
    RECT rgrc[3];  
    PWINDOWPOS lppos;  
} NCCALCSIZE_PARAMS;  
```  
  
#### <a name="parameters"></a>參數  
 *rgrc*  
 指定矩形的陣列。 第一個包含之已移動或調整大小的視窗新的座標。 移動或調整大小之前，第二個包含視窗的座標。 移動或調整大小之前，第三個包含視窗的用戶端區域的座標。 如果視窗是子視窗，座標是相對於父視窗工作區。 如果視窗是最上層視窗，座標是相對於螢幕。  
  
 *lppos*  
 指向[WINDOWPOS](../../mfc/reference/windowpos-structure1.md)結構，其中包含造成無法移動或調整視窗的作業中指定的大小和位置的值。  
  
## <a name="requirements"></a>需求  
 **標頭：** winuser.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)

