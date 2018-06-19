---
title: DELETEITEMSTRUCT 結構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- DELETEITEMSTRUCT
dev_langs:
- C++
helpviewer_keywords:
- DELETEITEMSTRUCT structure [MFC]
ms.assetid: 48d3998c-f4a8-402a-bf90-df3770a78685
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2f56a09742276c7fcb1bd66ff1a36b1d17cdf882
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370942"
---
# <a name="deleteitemstruct-structure"></a>DELETEITEMSTRUCT 結構
`DELETEITEMSTRUCT` 結構描述已刪除的主控描繪清單方塊或下拉式方塊項目。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct tagDELETEITEMSTRUCT { /* ditms */  
    UINT CtlType;  
    UINT CtlID;  
    UINT itemID;  
    HWND hwndItem;  
    UINT itemData;  
} DELETEITEMSTRUCT;  
```  
  
#### <a name="parameters"></a>參數  
 `CtlType`  
 指定**ODT_LISTBOX** （主控描繪清單方塊） 或**ODT_COMBOBOX** （主控描繪下拉式方塊）。  
  
 `CtlID`  
 指定清單方塊或下拉式方塊的識別項。  
  
 `itemID`  
 指定要移除之清單方塊或下拉式方塊中的項目索引。  
  
 `hwndItem`  
 識別控制項。  
  
 `itemData`  
 為項目指定應用程式定義的資料。 這個值會傳遞到中的控制項**lParam**參數，將項目加入清單方塊或下拉式方塊的訊息。  
  
## <a name="remarks"></a>備註  
 從清單方塊或下拉式方塊移除項目或者終結清單方塊或下拉式方塊時，Windows 會將 `WM_DELETEITEM` 訊息傳送給每個已刪除項目的擁有者。 **LParam**訊息參數包含此結構的指標。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem)


