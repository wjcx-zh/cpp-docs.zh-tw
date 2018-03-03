---
title: "WINDOWPLACEMENT 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- WINDOWPLACEMENT
dev_langs:
- C++
helpviewer_keywords:
- WINDOWPLACEMENT structure [MFC]
ms.assetid: ea7d61f6-eb57-478e-9b08-7c1d07091aa8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e73065cdf20d68b1da4ba77d1ad555e2bf95e937
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="windowplacement-structure"></a>WINDOWPLACEMENT 結構
`WINDOWPLACEMENT`結構包含在螢幕上視窗的位置之詳細資訊**。**  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct tagWINDOWPLACEMENT {     /* wndpl */  
    UINT length;  
    UINT flags;  
    UINT showCmd;  
    POINT ptMinPosition;  
    POINT ptMaxPosition;  
    RECT rcNormalPosition;  
} WINDOWPLACEMENT;  
```  
  
#### <a name="parameters"></a>參數  
 *length*  
 指定長度，以位元組為單位結構**。**  
  
 `flags`  
 指定旗標控制最小化的視窗與方法還原視窗的位置。 這個成員可以是下列其中一個或兩個下列旗標：  
  
- **WPF_SETMINPOSITION**指定 x-和 y-位置的最小化視窗，可以指定**。** 這個旗標必須指定座標在中設定**ptMinPosition**成員。  
  
- **WPF_RESTORETOMAXIMIZED**指定的 [還原] 視窗會最大化，不論它大化已最小化之前。 此設定無效，只還原視窗在下一次。 它不會變更預設的還原作業行為。 這個旗標時才有效唯一**SW_SHOWMINIMIZED**指定值**showCmd**成員。  
  
 *showCmd*  
 指定目前的視窗顯示狀態。 這個成員可以是下列值之一：  
  
- **SW_HIDE**隱藏視窗，並將啟用傳遞給另一個視窗。  
  
- **SW_MINIMIZE**指定的視窗最小化，並啟動系統的清單中的最上層視窗。  
  
- **SW_RESTORE**啟動並顯示視窗。 如果視窗是最小化或最大化，Windows 將它還原至其原始大小和位置 (相同**SW_SHOWNORMAL**)。  
  
- **SW_SHOW**啟動視窗並顯示在其目前大小和位置。  
  
- **Sw_showmaximized 其中一個**啟動視窗，顯示最大化視窗。  
  
- **SW_SHOWMINIMIZED**啟動視窗並將它顯示為圖示。  
  
- **SW_SHOWMINNOACTIVE**以圖示顯示視窗。 目前正在使用中視窗會保持有效。  
  
- **SW_SHOWNA**處於目前狀態會顯示視窗。 目前正在使用中視窗會保持有效。  
  
- **SW_SHOWNOACTIVATE**顯示視窗的最新的大小和位置。 目前正在使用中視窗會保持有效。  
  
- **SW_SHOWNORMAL**啟動並顯示視窗。 如果視窗是最小化或最大化，Windows 將它還原至其原始大小和位置 (相同**SW_RESTORE**)。  
  
 *ptMinPosition*  
 當視窗最小化時，請指定視窗的左上角的位置。  
  
 `ptMaxPosition`  
 最大化視窗時，請指定視窗的左上角的位置。  
  
 *rcNormalPosition*  
 當視窗處於正常 （還原） 的位置，請指定視窗的座標。  
  
## <a name="requirements"></a>需求  
 **標頭：** winuser.h  
  
## <a name="see-also"></a>請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::SetWindowPlacement](../../mfc/reference/cwnd-class.md#setwindowplacement)

