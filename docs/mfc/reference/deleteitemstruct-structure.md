---
title: "DELETEITEMSTRUCT 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DELETEITEMSTRUCT
dev_langs:
- C++
helpviewer_keywords:
- DELETEITEMSTRUCT structure
ms.assetid: 48d3998c-f4a8-402a-bf90-df3770a78685
caps.latest.revision: 13
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: f5936cbb863cf8ace851609cb1dc8352e21f9456
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

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



