---
title: "WINDOWPOS 結構&1; |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- WINDOWPOS
dev_langs:
- C++
helpviewer_keywords:
- WINDOWPOS structure
ms.assetid: a4ea7cd9-c4c2-4480-9c55-cbbff72195e1
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 522b15d630c3a5a3593010250db0491601493c69
ms.lasthandoff: 02/24/2017

---
# <a name="windowpos-structure1"></a>WINDOWPOS 結構&1;
`WINDOWPOS`結構包含大小和位置 視窗的相關資訊。  
  
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
 識別此視窗放置於背後的視窗。  
  
 *x*  
 指定視窗的左邊緣的位置。  
  
 *y*  
 指定視窗的右邊緣的位置。  
  
 `cx`  
 指定的視窗寬度，單位為像素。  
  
 `cy`  
 指定視窗的高度，單位為像素。  
  
 `flags`  
 指定視窗位置選項。 這個成員可以是下列值之一︰  
  
- **SWP_DRAWFRAME**視窗周圍繪製 （定義於視窗類別描述） 的框架。 視窗收到`WM_NCCALCSIZE`訊息。  
  
- **SWP_FRAMECHANGED**傳送`WM_NCCALCSIZE`訊息 視窗中，即使未變更視窗的大小。 如果未指定這個旗標，`WM_NCCALCSIZE`視窗的大小變更時，才會傳送。  
  
- **SWP_HIDEWINDOW**隱藏視窗。  
  
- `SWP_NOACTIVATE`無法啟動視窗。  
  
- **SWP_NOCOPYBITS**捨棄工作區的整個內容。 如果未指定這個旗標，有效的工作區的內容會儲存及之後的視窗大小或重新定位複製回用戶端區域。  
  
- `SWP_NOMOVE`保留目前的位置 (忽略**x**和**y**成員)。  
  
- **SWP_NOOWNERZORDER**不會變更擁有者視窗的疊置順序的位置。  
  
- `SWP_NOSIZE`保留目前的大小 (忽略**cx**和**cy**成員)。  
  
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


