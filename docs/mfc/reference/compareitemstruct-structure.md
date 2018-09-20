---
title: COMPAREITEMSTRUCT 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COMPAREITEMSTRUCT
dev_langs:
- C++
helpviewer_keywords:
- COMPAREITEMSTRUCT structure [MFC]
ms.assetid: 4b7131a5-5c7d-4e98-aac7-e85650262b52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 450e6fa4694c35929196cc5df3bf2fd6b4e843c4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46406818"
---
# <a name="compareitemstruct-structure"></a>COMPAREITEMSTRUCT 結構

`COMPAREITEMSTRUCT`結構提供的識別項和應用程式提供兩個項目已排序的主控描繪清單方塊或下拉式方塊中的資料。

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

*CtlType*<br/>
ODT_LISTBOX （可指定主控描繪清單方塊） 或 ODT_COMBOBOX （可指定主控描繪下拉式方塊）。

*CtlID*<br/>
清單方塊或下拉式方塊控制項識別碼。

*hwndItem*<br/>
控制項的視窗控制代碼。

*itemID1*<br/>
在清單方塊或下拉式方塊要比較的第一個項目索引。

*itemData1*<br/>
應用程式提供要比較的第一個項目資料。 將項目加入至下拉式方塊或清單方塊的呼叫中傳遞此值。

*itemID2*<br/>
在清單方塊或下拉式方塊所比較之第二個項目的索引。

*itemData2*<br/>
應用程式提供要比較的第二個項目資料。 將項目加入至下拉式方塊或清單方塊的呼叫中傳遞此值。

## <a name="remarks"></a>備註

只要應用程式會將新的項目新增至主控描繪清單方塊或下拉式方塊以 CBS_SORT 或 LBS_SORT 樣式，Windows 會將擁有者傳送 WM_COMPAREITEM 訊息。 *LParam*訊息參數中包含的長指標`COMPAREITEMSTRUCT`結構。 在收到訊息時，擁有者會比較兩個項目，並傳回值，指出哪一個項目排序在其他。

## <a name="requirements"></a>需求

**標頭：** winuser.h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem)

