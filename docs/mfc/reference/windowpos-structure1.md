---
title: "WINDOWPOS 結構 1 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: WINDOWPOS
dev_langs: C++
helpviewer_keywords: WINDOWPOS structure [MFC]
ms.assetid: a4ea7cd9-c4c2-4480-9c55-cbbff72195e1
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1191b79063684ec306ad9595251d1d35da296cba
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="windowpos-structure1"></a>WINDOWPOS 結構 1
`WINDOWPOS`結構包含之大小和視窗的位置相關資訊。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct tagWINDOWPOS { /* wp */  
    HWND hwnd;  
    HWND hwndInsertAfter;  
    int x;  
    int y;  
    int cx;  
    int cy;  
    UINT flags;  
} WINDOWPOS;  
```  
  
#### <a name="parameters"></a>參數  
 *hwnd*  
 識別視窗。  
  
 *hwndInsertAfter*  
 識別其後放置於此視窗的視窗。  
  
 *x*  
 指定視窗的左邊緣位置。  
  
 *y*  
 指定視窗的右邊緣的位置。  
  
 `cx`  
 指定的視窗寬度，單位為像素。  
  
 `cy`  
 指定視窗的高度，單位為像素。  
  
 `flags`  
 指定視窗位置選項。 這個成員可以是下列值之一：  
  
- **SWP_DRAWFRAME**繪製視窗周圍框架 （定義於類別描述視窗）。 視窗收到`WM_NCCALCSIZE`訊息。  
  
- **SWP_FRAMECHANGED**傳送`WM_NCCALCSIZE`訊息視窗中，即使不變更視窗的大小。 如果未指定這個旗標，`WM_NCCALCSIZE`視窗的大小已經變更時，才會傳送。  
  
- **SWP_HIDEWINDOW**隱藏視窗。  
  
- `SWP_NOACTIVATE`不會啟動視窗。  
  
- **SWP_NOCOPYBITS**捨棄工作區的整個內容。 如果未指定這個旗標，用戶端區域的有效內容所儲存且之後視窗大小或重新調整位置複製到工作區。  
  
- `SWP_NOMOVE`保留目前的位置 (會忽略**x**和**y**成員)。  
  
- **SWP_NOOWNERZORDER**不會變更圖層順序中的主控視窗的位置。  
  
- `SWP_NOSIZE`會保留目前的大小 (會忽略**cx**和**cy**成員)。  
  
- **SWP_NOREDRAW**不會重新繪製的變更。  
  
- **SWP_NOREPOSITION**相同**SWP_NOOWNERZORDER**。  
  
- **SWP_NOSENDCHANGING**防止接收視窗`WM_WINDOWPOSCHANGING`訊息。  
  
- `SWP_NOZORDER`會保留目前的順序 (會忽略**hwndInsertAfter**成員)。  
  
- **SWP_SHOWWINDOW**顯示視窗。  
  
## <a name="requirements"></a>需求  
 **標頭：** winuser.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging)

