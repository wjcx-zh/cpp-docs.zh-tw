---
title: "WINDOWPLACEMENT 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- WINDOWPLACEMENT
dev_langs:
- C++
helpviewer_keywords:
- WINDOWPLACEMENT structure
ms.assetid: ea7d61f6-eb57-478e-9b08-7c1d07091aa8
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
ms.openlocfilehash: 62cf7003f43d50d5998dd527ae5ad7b10ab95686
ms.lasthandoff: 02/24/2017

---
# <a name="windowplacement-structure"></a>WINDOWPLACEMENT 結構
`WINDOWPLACEMENT`結構包含在螢幕上視窗的詳細資訊**。**  
  
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
 指定旗標可控制最小化的視窗和還原視窗的方法的位置。 這個成員可以是其中一個或多個下列旗標︰  
  
- **WPF_SETMINPOSITION**指定 x-和 y-位置的最小化視窗，可以指定**。** 這個旗標必須是指定是否座標設定**ptMinPosition**成員。  
  
- **WPF_RESTORETOMAXIMIZED**指定，還原的視窗會最大化，不論它大化之前已降至最低。 這項設定正確。 只能在下一次還原視窗 它不會變更預設還原行為。 這個旗標是時才有效**SW_SHOWMINIMIZED**為指定值**showCmd**成員。  
  
 *showCmd*  
 指定目前的視窗顯示狀態。 這個成員可以是下列值之一︰  
  
- **SW_HIDE**隱藏視窗，並將啟用傳遞至另一個視窗。  
  
- **SW_MINIMIZE**指定的視窗最小化，並啟動系統的清單中的最上層視窗。  
  
- **SW_RESTORE**啟動以及顯示的視窗。 如果視窗是最小化或最大化時，Windows 將它還原至其原始大小和位置 (與相同**SW_SHOWNORMAL**)。  
  
- **SW_SHOW**啟動視窗，並顯示在其目前的大小和位置。  
  
- **SW_SHOWMAXIMIZED**啟動視窗，顯示最大化視窗。  
  
- **SW_SHOWMINIMIZED**啟動視窗，顯示為圖示。  
  
- **SW_SHOWMINNOACTIVE**以圖示顯示的視窗。 目前使用中視窗保持作用中。  
  
- **SW_SHOWNA**處於目前狀態顯示的視窗。 目前使用中視窗保持作用中。  
  
- **SW_SHOWNOACTIVATE**顯示視窗的最新的大小和位置。 目前使用中視窗保持作用中。  
  
- **SW_SHOWNORMAL**啟動以及顯示的視窗。 如果視窗是最小化或最大化時，Windows 將它還原至其原始大小和位置 (與相同**SW_RESTORE**)。  
  
 *ptMinPosition*  
 當視窗最小化時，請指定視窗的左上角的位置。  
  
 `ptMaxPosition`  
 當視窗最大化時，請指定視窗的左上角的位置。  
  
 *rcNormalPosition*  
 當視窗在正常 （還原） 的位置，請指定視窗的座標。  
  
## <a name="requirements"></a>需求  
 **標頭：** winuser.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::SetWindowPlacement](../../mfc/reference/cwnd-class.md#setwindowplacement)


