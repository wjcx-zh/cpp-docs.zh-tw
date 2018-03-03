---
title: "COMPAREITEMSTRUCT 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- COMPAREITEMSTRUCT
dev_langs:
- C++
helpviewer_keywords:
- COMPAREITEMSTRUCT structure [MFC]
ms.assetid: 4b7131a5-5c7d-4e98-aac7-e85650262b52
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7903e51a83533c8f2458c4400c64717021a1ccb8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compareitemstruct-structure"></a>COMPAREITEMSTRUCT 結構
`COMPAREITEMSTRUCT`結構提供的識別項和應用程式提供兩個項目的已排序的主控描繪清單方塊或下拉式方塊中的資料。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct tagCOMPAREITEMSTRUCT {  
    UINT CtlType;  
    UINT CtlID;  
    HWND hwndItem;  
    UINT itemID1;  
    DWORD itemData1;  
    UINT itemID2;  
    DWORD itemData2;  
} COMPAREITEMSTRUCT;  
```  
  
#### <a name="parameters"></a>參數  
 `CtlType`  
 **ODT_LISTBOX** （指定主控描繪清單方塊） 或**ODT_COMBOBOX** （指定主控描繪下拉式方塊）。  
  
 `CtlID`  
 清單方塊或下拉式方塊控制項 ID。  
  
 `hwndItem`  
 控制項的視窗控制代碼。  
  
 *itemID1*  
 在清單方塊或下拉式方塊所比較的第一個項目索引。  
  
 *itemData1*  
 要比較的第一個項目的應用程式提供資料。 將項目加入至組合或清單方塊的呼叫中傳遞此值。  
  
 *itemID2*  
 在清單方塊或下拉式方塊所比較的第二個項目索引。  
  
 *itemData2*  
 應用程式提供的資料進行比較的第二個項目。 將項目加入至組合或清單方塊的呼叫中傳遞此值。  
  
## <a name="remarks"></a>備註  
 每當應用程式會將新的項目加入至主控描繪清單方塊或下拉式方塊以建立**CBS_SORT**或**LBS_SORT**樣式，Windows 會傳送擁有者`WM_COMPAREITEM`訊息。 `lParam`訊息參數包含的長指標`COMPAREITEMSTRUCT`結構。 收到訊息時，擁有者會比較兩個項目，並傳回值，指出哪一個項目排序之前另。  
  
## <a name="requirements"></a>需求  
 **標頭：** winuser.h  
  
## <a name="see-also"></a>請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem)

