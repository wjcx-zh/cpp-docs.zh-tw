---
title: MINMAXINFO 結構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- MINMAXINFO
dev_langs:
- C++
helpviewer_keywords:
- MINMAXINFO structure [MFC]
ms.assetid: be6fb578-f98a-4581-9ada-be9df308ed2f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 12161938f96e5044ae48f9eb5cf380fbc3840d3f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="minmaxinfo-structure"></a>MINMAXINFO 結構
`MINMAXINFO`結構包含以最大化視窗的大小和位置和大小的最小和最大追蹤相關資訊。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct tagMINMAXINFO {  
    POINT ptReserved;  
    POINT ptMaxSize;  
    POINT ptMaxPosition;  
    POINT ptMinTrackSize;  
    POINT ptMaxTrackSize;  
} MINMAXINFO;  
```  
  
#### <a name="parameters"></a>參數  
 *ptReserved*  
 保留供內部使用。  
  
 *ptMaxSize*  
 指定最大化的寬度 (point.x) 和視窗最大化的高度 (point.y)。  
  
 `ptMaxPosition`  
 指定最大化的視窗 (point.x) 左邊的位置和最大化的視窗 (point.y) 頂端的位置。  
  
 *ptMinTrackSize*  
 指定的最小追蹤寬度 (point.x)，追蹤視窗的高度 (point.y) 最小值。  
  
 *ptMaxTrackSize*  
 指定追蹤寬度 (point.x) 的最大值和追蹤的視窗的高度 (point.y) 的最大值。  
  
## <a name="requirements"></a>需求  
 **標頭：** winuser.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)

