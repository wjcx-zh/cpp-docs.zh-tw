---
title: DELETEITEMSTRUCT 結構
ms.date: 11/04/2016
f1_keywords:
- DELETEITEMSTRUCT
helpviewer_keywords:
- DELETEITEMSTRUCT structure [MFC]
ms.assetid: 48d3998c-f4a8-402a-bf90-df3770a78685
ms.openlocfilehash: dd1f48fd584016dab740bc8a6bd05ff3b756e41b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486875"
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

*CtlType*<br/>
指定 ODT_LISTBOX （主控描繪清單方塊） 或 ODT_COMBOBOX （主控描繪下拉式方塊）。

*CtlID*<br/>
指定清單方塊或下拉式方塊的識別項。

*項目識別碼*<br/>
指定要移除之清單方塊或下拉式方塊中的項目索引。

*hwndItem*<br/>
識別控制項。

*itemData*<br/>
為項目指定應用程式定義的資料。 此值傳遞到中的控制項*lParam*參數，將項目加入清單方塊或下拉式方塊的訊息。

## <a name="remarks"></a>備註

從清單方塊或下拉式方塊或終結清單方塊或下拉式方塊移除項目時，Windows 會傳送 WM_DELETEITEM 訊息給每個已刪除的項目擁有者。 *LParam*訊息參數包含此結構的指標。

## <a name="requirements"></a>需求

**標題:** atldbcli.h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem)

