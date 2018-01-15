---
title: "DRAWITEMSTRUCT 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DRAWITEMSTRUCT
dev_langs: C++
helpviewer_keywords: DRAWITEMSTRUCT structure [MFC]
ms.assetid: ba9ef1d4-aebb-45e9-b956-4b81a02e50f7
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 438d698b486b455d7898a836d510aa5ec1c6e454
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="drawitemstruct-structure"></a>DRAWITEMSTRUCT 結構
`DRAWITEMSTRUCT` 結構提供主控視窗判斷如何繪製主控描繪控制項或功能表項目時必須具有的資訊。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct tagDRAWITEMSTRUCT {  
    UINT CtlType;  
    UINT CtlID;  
    UINT itemID;  
    UINT itemAction;  
    UINT itemState;  
    HWND hwndItem;  
    HDC hDC;  
    RECT rcItem;  
    DWORD itemData;  
} DRAWITEMSTRUCT;  
```  
  
#### <a name="parameters"></a>參數  
 `CtlType`  
 控制項類型。 控制項類型的值如下：  
  
- **ODT_BUTTON** 主控描繪按鈕  
  
- **ODT_COMBOBOX** 主控描繪下拉式方塊  
  
- **ODT_LISTBOX** 主控描繪清單方塊  
  
- **ODT_MENU** 主控描繪功能表  
  
- **ODT_LISTVIEW** 清單檢視控制項  
  
- **ODT_STATIC** 主控描繪靜態控制項  
  
- **ODT_TAB** 索引標籤控制項  
  
 `CtlID`  
 下拉式方塊、清單方塊或按鈕的控制項識別碼。 這個成員無法用於功能表。  
  
 `itemID`  
 功能表或清單方塊或下拉式方塊中之項目索引功能表的項目識別碼。 對於空的清單方塊或下拉式方塊，這個成員是一個負數值，它允許應用程式只在 **rcItem** 成員所指定的座標上繪製焦點矩形，即使是控制項中沒有任何項目。 使用者可以因此看到清單方塊或下拉式方塊是否擁有輸入焦點。 **itemAction** 成員中的位元設定會決定是否要如同清單方塊或下拉式方塊具有輸入焦點一樣地繪製矩形。  
  
 `itemAction`  
 定義所需的繪圖動作。 這將是一或多個下列位元：  
  
- **ODA_DRAWENTIRE** 需要繪製整個控制項時，設定此位元。  
  
- **ODA_FOCUS** 控制項獲得或失去輸入焦點時，設定此位元。 應該檢查 **itemState** 成員以判斷控制項是否具有焦點。  
  
- **ODA_SELECT** 僅在選取狀態變更時，設定此位元。 應該檢查 **itemState** 成員以判斷新的選取狀態。  
  
 *itemState*  
 指定在目前的繪圖動作發生之後，項目的視覺狀態。 也就是說，如果功能表項目要呈現灰色，則將狀態旗標設定為 **ODS_GRAYED** 。 狀態旗標如：  
  
- **ODS_CHECKED** 如果要檢查功能表項目，則設定此位元。 此位元只用在功能表中。  
  
- **ODS_DISABLED** 如果項目要繪製為停用，則設定此位元。  
  
- **ODS_FOCUS** 如果項目具有輸入焦點，則設定此位元。  
  
- **ODS_GRAYED** 如果項目要呈現為灰色，則設定此位元。 此位元只用在功能表中。  
  
- **ODS_SELECTED** 如果項目的狀態為已選取，則設定此位元。  
  
- **ODS_COMBOBOXEDIT** 繪圖發生在主控繪製下拉式方塊的選取項目欄位 (編輯控制項) 中。  
  
- **ODS_DEFAULT** 項目是預設項目。  
  
 `hwndItem`  
 指定下拉式方塊、清單方塊和按鈕之控制項的視窗控制代碼。 指定包含功能表項目之功能表 (`HMENU`) 的控制代碼。  
  
 `hDC`  
 識別裝置內容。 對控制項執行繪圖作業時，必須使用這個裝置內容。  
  
 *rcItem*  
 在 `hDC` 成員所指定裝置內容中的矩形，定義要繪製之控制項的邊界。 Windows 會自動裁剪擁有者在下拉式方塊、清單方塊和按鈕的裝置內容中繪製的任何項目，但它不會裁剪功能表項目。 繪製功能表項目時，擁有者不能在 **rcItem** 成員所定義的矩形界限之外繪製。  
  
 `itemData`  
 對於下拉式方塊或清單方塊，這個成員會包含已由下列其中一項傳遞至清單方塊的值：  
  
- [CComboBox::AddString](../../mfc/reference/ccombobox-class.md#addstring)  
  
- [CComboBox::InsertString](../../mfc/reference/ccombobox-class.md#insertstring)  
  
- [CListBox::AddString](../../mfc/reference/clistbox-class.md#addstring)  
  
- [CListBox::InsertString](../../mfc/reference/clistbox-class.md#insertstring)  
  
 對於功能表，這個成員會包含已由下列其中一項傳遞至功能表的值：  
  
- [CMenu::AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu)  
  
- [CMenu::InsertMenu](../../mfc/reference/cmenu-class.md#insertmenu)  
  
- [CMenu::ModifyMenu](../../mfc/reference/cmenu-class.md#modifymenu)  
  
## <a name="remarks"></a>備註  
 主控描繪控制項或功能表項目的主控視窗會以 `lParam` 訊息的 `WM_DRAWITEM` 參數，收到此結構的指標。  
  
## <a name="requirements"></a>需求  
 **標頭：** winuser.h  
  
## <a name="see-also"></a>請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem)

