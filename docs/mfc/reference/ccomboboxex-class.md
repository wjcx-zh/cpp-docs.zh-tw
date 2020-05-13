---
title: CComboBoxEx 類別
ms.date: 11/04/2016
f1_keywords:
- CComboBoxEx
- AFXCMN/CComboBoxEx
- AFXCMN/CComboBoxEx::CComboBoxEx
- AFXCMN/CComboBoxEx::Create
- AFXCMN/CComboBoxEx::CreateEx
- AFXCMN/CComboBoxEx::DeleteItem
- AFXCMN/CComboBoxEx::GetComboBoxCtrl
- AFXCMN/CComboBoxEx::GetEditCtrl
- AFXCMN/CComboBoxEx::GetExtendedStyle
- AFXCMN/CComboBoxEx::GetImageList
- AFXCMN/CComboBoxEx::GetItem
- AFXCMN/CComboBoxEx::HasEditChanged
- AFXCMN/CComboBoxEx::InsertItem
- AFXCMN/CComboBoxEx::SetExtendedStyle
- AFXCMN/CComboBoxEx::SetImageList
- AFXCMN/CComboBoxEx::SetItem
- AFXCMN/CComboBoxEx::SetWindowTheme
helpviewer_keywords:
- CComboBoxEx [MFC], CComboBoxEx
- CComboBoxEx [MFC], Create
- CComboBoxEx [MFC], CreateEx
- CComboBoxEx [MFC], DeleteItem
- CComboBoxEx [MFC], GetComboBoxCtrl
- CComboBoxEx [MFC], GetEditCtrl
- CComboBoxEx [MFC], GetExtendedStyle
- CComboBoxEx [MFC], GetImageList
- CComboBoxEx [MFC], GetItem
- CComboBoxEx [MFC], HasEditChanged
- CComboBoxEx [MFC], InsertItem
- CComboBoxEx [MFC], SetExtendedStyle
- CComboBoxEx [MFC], SetImageList
- CComboBoxEx [MFC], SetItem
- CComboBoxEx [MFC], SetWindowTheme
ms.assetid: 33ca960a-2409-478c-84a4-a2ee8ecfe8f7
ms.openlocfilehash: a948d54be17103fa83848ff5f0e86dd2c522f0a3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754819"
---
# <a name="ccomboboxex-class"></a>CComboBoxEx 類別

藉由提供影像清單的支援，擴充下拉式方塊控制項。

## <a name="syntax"></a>語法

```
class CComboBoxEx : public CComboBox
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComboBoxEx:CComboBoxEx](#ccomboboxex)|建構 `CComboBoxEx` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComboBoxEx:建立](#create)|創建組合框並將其附加到`CComboBoxEx`物件。|
|[CComboBoxEx:建立Ex](#createex)|創建具有指定 Windows 擴充樣式的組合框並將`ComboBoxEx`其附加到 物件。|
|[CComboBoxEx::Delete專案](#deleteitem)|從控制項中移除項目`ComboBoxEx`。|
|[CComboBoxEx:取得ComboBoxCtrl](#getcomboboxctrl)|檢索指向子組合框控件的指標。|
|[CComboBoxEx:取得編輯](#geteditctrl)|檢索控件的編輯控制項部分的`ComboBoxEx`句柄。|
|[CComboBoxEx:取得延伸樣式](#getextendedstyle)|檢索控件正在使用的`ComboBoxEx`擴展樣式。|
|[CComboBoxEx:抓取圖片清單](#getimagelist)|檢索分配給控制件的圖像清單的`ComboBoxEx`指標。|
|[CComboBoxEx:取得項目](#getitem)|檢索給定`ComboBoxEx`項的項資訊。|
|[CComboBoxEx::已編輯](#haseditchanged)|通過鍵入確定使用者是否更改了`ComboBoxEx`編輯控制件的內容。|
|[CComboBoxEx:插入專案](#insertitem)|在控制項中`ComboBoxEx`插入新專案。|
|[CComboBoxEx::設定延伸樣式](#setextendedstyle)|在`ComboBoxEx`控件中設置擴展樣式。|
|[CComboBoxEx::設定影像清單](#setimagelist)|為`ComboBoxEx`控制項設定影像清單。|
|[CComboBoxEx:設定項目](#setitem)|設置`ComboBoxEx`控項中項的屬性。|
|[CComboBoxEx::設定視窗主題](#setwindowtheme)|設置擴展組合框控件的視覺樣式。|

## <a name="remarks"></a>備註

通過使用`CComboBoxEx`創建組合框控制項,您不再需要實現自己的圖像繪製代碼。 而是使用`CComboBoxEx`來訪問圖像清單中的圖像。

## <a name="image-list-support"></a>影像清單支援

在標準組合框中,組合框的所有者負責通過將組合框創建為所有者繪製控制件來繪製圖像。 使用`CComboBoxEx`時,不需要將繪圖樣式CBS_OWNERDRAWFIXED設置,並且CBS_HASSTRINGS,因為它們是隱含的。 否則,必須編寫代碼以執行繪圖操作。 控件`CComboBoxEx`每專案最多支援三個圖像:一個用於選定狀態,一個用於未選中狀態,一個用於疊加圖像。

## <a name="styles"></a>樣式

`CComboBoxEx`支援CBS_SIMPLE、CBS_DROPDOWN、CBS_DROPDOWNLIST和WS_CHILD樣式。 控制項會忽略建立視窗時傳遞的所有其他樣式。 創建視窗後,可以通過調`CComboBoxEx`用 成員函數[SetExtendedStyle](#setextendedstyle)提供其他組合框樣式。 使用這些樣式,您可以:

- 將清單中的字串搜尋設定為區分大小寫。

- 建立組合框控制項,該控制項使用斜杠 ('/')、反斜\\杠 ('') 和句點 ('.') 字元作為單詞分隔符。 這允許使用者使用鍵盤快速鍵 CTRL+ 箭頭從一字跳一字。

- 將組合框控制項設定為顯示或不顯示影像。 如果未顯示圖像,組合框可以刪除容納圖像的文本縮進。

- 創建一個狹窄的組合框控制項,包括調整大小,以便它剪輯它包含的更寬組合框。

這些樣式標誌在[使用 CComboBoxEx](../../mfc/using-ccomboboxex.md)中進一步描述。

## <a name="item-retention-and-callback-item-attributes"></a>專案保留與回檔項目屬性

專案資訊(如項和圖像的索引、縮進值和文字字串)存儲在 Win32 結構[COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw)中,如 Windows SDK 中所述。 結構還包含對應於回調標誌的成員。

有關詳細的概念性討論,請參閱[使用 CComboBoxEx](../../mfc/using-ccomboboxex.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CComboBox](../../mfc/reference/ccombobox-class.md)

`CComboBoxEx`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

## <a name="ccomboboxexccomboboxex"></a><a name="ccomboboxex"></a>CComboBoxEx:CComboBoxEx

呼叫此成員函式以建立物件`CComboBoxEx`。

```
CComboBoxEx();
```

## <a name="ccomboboxexcreate"></a><a name="create"></a>CComboBoxEx:建立

創建組合框並將其附加到`CComboBoxEx`物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定應用於組合框的組合框樣式的組合。 關於樣式的詳細資訊,請參閱下面的**備註**。

*矩形*<br/>
對[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](/windows/win32/api/windef/ns-windef-rect)結構的引用,即組合框的位置和大小。

*pparentwnd*<br/>
指向作為組合框的父視窗(通常為`CDialog`) 的[CWnd](../../mfc/reference/cwnd-class.md)物件的指標。 它不得為 NULL。

*nID*<br/>
指定組合框的控制 ID。

### <a name="return-value"></a>傳回值

如果物件已成功創建,則非零;否則 0。

### <a name="remarks"></a>備註

通過兩`CComboBoxEx`個步驟建立物件:

1. 調用[CComboBoxEx](#ccomboboxex)`CComboBoxEx`建構 物件。

1. 呼叫此成員函數,該函數創建擴展的 Windows 組合框並將其`CComboBoxEx`附加到 物件。

調用`Create`時 ,MFC 將初始化公共控件。

建立組合框時,可以指定以下任何或所有組合框樣式:

- CBS_SIMPLE

- CBS_DROPDOWN

- CBS_DROPDOWNLIST

- CBS_AUTOHSCROLL

- WS_CHILD

建立視窗時傳遞的所有其他樣式將被忽略。 該`ComboBoxEx`控件還支援提供其他功能的擴展樣式。 這些樣式在[ComboBoxEx 控制項擴充樣式](/windows/win32/Controls/comboboxex-control-extended-styles)中(Windows SDK)中描述。 通過調用 Set[擴展樣式](#setextendedstyle)來設置這些樣式。

如果要將延伸視窗樣式與控制項一起使用,請呼叫[CreateEx](#createex)`Create`而不是 。

## <a name="ccomboboxexcreateex"></a><a name="createex"></a>CComboBoxEx:建立Ex

呼叫此函數以建立擴充組合框控制項(子視窗),並將其`CComboBoxEx`與物件關聯。

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwExStyle*<br/>
指定要創建的控制項的擴充樣式。 有關擴展 Windows 樣式的清單,請參閱 Windows SDK 中[創建 WindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*參數。

*dwStyle*<br/>
組合框控件的樣式。 請參閱[創建](#create)樣式清單。

*矩形*<br/>
對[RECT](/windows/win32/api/windef/ns-windef-rect)結構的引用,描述要創建的視窗的大小和位置,在*pParentWnd*的用戶端座標中。

*pparentwnd*<br/>
指向控件的父視窗的指標。

*nID*<br/>
控制項的子視窗 ID。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

使用`CreateEx``Create`而不是應用擴展的 Windows 樣式,由 Windows 擴充樣式前言**WS_EX_** 指定。

`CreateEx`使用*dwExStyle*指定的擴展 Windows 樣式創建控制項。 您必須使用[Set 擴充樣式](#setextendedstyle)設定特定於延伸組合框控制元件的擴充樣式。 例如,用於`CreateEx`將此類樣式設置為WS_EX_CONTEXTHELP,但用於`SetExtendedStyle`將此類樣式設置為CBES_EX_CASESENSITIVE。 有關詳細資訊,請參閱 Windows SDK 中的主題[ComboBoxEx 控制項擴充樣式中描述的樣式](/windows/win32/Controls/comboboxex-control-extended-styles)。

## <a name="ccomboboxexdeleteitem"></a><a name="deleteitem"></a>CComboBoxEx::Delete專案

從控制項中移除項目`ComboBoxEx`。

```
int DeleteItem(int iIndex);
```

### <a name="parameters"></a>參數

*iIndex*<br/>
要刪除的項的從零開始索引。

### <a name="return-value"></a>傳回值

控件中剩餘的項數。 如果*iIndex*無效,則函數將返回CB_ERR。

### <a name="remarks"></a>備註

此成員函數實現消息[CBEM_DELETEITEM](/windows/win32/Controls/cbem-deleteitem)的功能,如 Windows SDK 中所述。 當您調用 DeleteItem 時,帶有CBEN_DELETEITEM通知[的WM_NOTIFY](/windows/win32/controls/wm-notify)消息將發送到父視窗。

## <a name="ccomboboxexgetcomboboxctrl"></a><a name="getcomboboxctrl"></a>CComboBoxEx:取得ComboBoxCtrl

呼叫此成員函數以獲取指向物件中的組合框控制項的`CComboBoxEx`指標。

```
CComboBox* GetComboBoxCtrl();
```

### <a name="return-value"></a>傳回值

`CComboBox` 物件的指標。

### <a name="remarks"></a>備註

這個`CComboBoxEx`控制器由父視窗組成, 這個視窗封裝`CComboBox`。

返回`CComboBox`值指向的對像是臨時物件,並在下一個空閒處理期間銷毀。

## <a name="ccomboboxexgeteditctrl"></a><a name="geteditctrl"></a>CComboBoxEx:取得編輯

呼叫此成員函數以獲取指向組合框的編輯控制項的指標。

```
CEdit* GetEditCtrl();
```

### <a name="return-value"></a>傳回值

指向[CEdit](../../mfc/reference/cedit-class.md)物件的指標。

### <a name="remarks"></a>備註

使用`CComboBoxEx`CBS_DROPDOWN樣式創建控制項時,將使用編輯框。

返回`CEdit`值指向的對像是臨時物件,並在下一個空閒處理期間銷毀。

## <a name="ccomboboxexgetextendedstyle"></a><a name="getextendedstyle"></a>CComboBoxEx:取得延伸樣式

調用此成員函數獲取用於控制項的`CComboBoxEx`擴充樣式。

```
DWORD GetExtendedStyle() const;
```

### <a name="return-value"></a>傳回值

包含用於組合框控件的擴展樣式的 DWORD 值。

### <a name="remarks"></a>備註

有關這些樣式的詳細資訊,請參閱 Windows SDK 中的[ComboBoxEx 控制項延伸樣式](/windows/win32/Controls/comboboxex-control-extended-styles)。

## <a name="ccomboboxexgetimagelist"></a><a name="getimagelist"></a>CComboBoxEx:抓取圖片清單

呼叫此成員函數以獲取指向控制項使用的影像清單的`CComboBoxEx`指標。

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>傳回值

指向[CImageList](../../mfc/reference/cimagelist-class.md)物件的指標。 如果失敗,此成員函數將返回 NULL。

### <a name="remarks"></a>備註

返回`CImageList`值指向的對像是臨時物件,並在下一個空閒處理期間銷毀。

## <a name="ccomboboxexgetitem"></a><a name="getitem"></a>CComboBoxEx:取得項目

檢索給定`ComboBoxEx`項的項資訊。

```
BOOL GetItem(COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>參數

*pCB 專案*<br/>
指向將接收物料資訊的[COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw)結構的指標。

### <a name="return-value"></a>傳回值

如果操作成功,則非零;否則 0。

### <a name="remarks"></a>備註

此成員函數實現消息[CBEM_GETITEM](/windows/win32/Controls/cbem-getitem)的功能,如 Windows SDK 中所述。

## <a name="ccomboboxexhaseditchanged"></a><a name="haseditchanged"></a>CComboBoxEx::已編輯

通過鍵入確定使用者是否更改了`ComboBoxEx`編輯控制件的內容。

```
BOOL HasEditChanged();
```

### <a name="return-value"></a>傳回值

如果使用者在控件的編輯框中鍵入了非零;如果使用者在控件的編輯框中鍵入了「非零」;否則 0。

### <a name="remarks"></a>備註

此成員函數實現消息[CBEM_HASEDITCHANGED](/windows/win32/Controls/cbem-haseditchanged)的功能,如 Windows SDK 中所述。

## <a name="ccomboboxexinsertitem"></a><a name="insertitem"></a>CComboBoxEx:插入專案

在控制項中`ComboBoxEx`插入新專案。

```
int InsertItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>參數

*pCB 專案*<br/>
指向將接收物料資訊的[COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw)結構的指標。 此結構包含項的回調標誌值。

### <a name="return-value"></a>傳回值

如果成功,則插入新專案的索引;否則 -1。

### <a name="remarks"></a>備註

調用`InsertItem`時,將發送帶有[CBEN_INSERTITEM](/windows/win32/Controls/cben-insertitem)通知[WM_NOTIFY](/windows/win32/controls/wm-notify)消息到父視窗。

## <a name="ccomboboxexsetextendedstyle"></a><a name="setextendedstyle"></a>CComboBoxEx::設定延伸樣式

調用此成員函數以設置用於組合框擴展控制項的擴充樣式。

```
DWORD SetExtendedStyle(
    DWORD dwExMask,
    DWORD dwExStyles);
```

### <a name="parameters"></a>參數

*dwExMask*<br/>
DWORD 值,指示*dwExStyles*中的哪些樣式將受到影響。 只有*dwExMask*中的擴展樣式才會更改。 所有其他樣式將保持不變。 如果此參數為零,則*dwExStyles*中的所有樣式都將受到影響。

*dwExStyles*<br/>
包含組合框控制式模組延伸樣式的 DWORD 值,用於為控制項設定。

### <a name="return-value"></a>傳回值

包含以前用於控制項的擴展樣式的 DWORD 值。

### <a name="remarks"></a>備註

有關這些樣式的詳細資訊,請參閱 Windows SDK 中的[ComboBoxEx 控制項延伸樣式](/windows/win32/Controls/comboboxex-control-extended-styles)。

要使用延伸視窗樣式建立組合框延伸控制項,請使用[CreateEx](#createex)。

## <a name="ccomboboxexsetimagelist"></a><a name="setimagelist"></a>CComboBoxEx::設定影像清單

為`ComboBoxEx`控制項設定影像清單。

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>參數

*pImageList*<br/>
指向包含要與`CImageList`控制項一起使用的圖像的物件的`CComboBoxEx`指標。

### <a name="return-value"></a>傳回值

指向[CImageList](../../mfc/reference/cimagelist-class.md)物件的指標,其中`CComboBoxEx`包含控制項以前使用的圖像。 如果以前未設置任何圖像清單,則為 NULL。

### <a name="remarks"></a>備註

此成員函數實現消息[CBEM_SETIMAGELIST](/windows/win32/Controls/cbem-setimagelist)的功能,如 Windows SDK 中所述。 如果更改預設編輯控制檔的高度,請呼叫 Win32 函數[SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos)`SetImageList`來調整呼叫 後控制的大小,否則控制項將無法正確顯示。

返回`CImageList`值指向的對像是臨時物件,並在下一個空閒處理期間銷毀。

## <a name="ccomboboxexsetitem"></a><a name="setitem"></a>CComboBoxEx:設定項目

設置`ComboBoxEx`控項中項的屬性。

```
BOOL SetItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>參數

*pCB 專案*<br/>
指向將接收物料資訊的[COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw)結構的指標。

### <a name="return-value"></a>傳回值

如果操作成功,則非零;否則 0。

### <a name="remarks"></a>備註

此成員函數實現消息[CBEM_SETITEM](/windows/win32/Controls/cbem-setitem)的功能,如 Windows SDK 中所述。

## <a name="ccomboboxexsetwindowtheme"></a><a name="setwindowtheme"></a>CComboBoxEx::設定視窗主題

設置擴展組合框控件的視覺樣式。

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>參數

*pssSubApp 名稱*<br/>
指向要設定的擴展組合框可視樣式的 Unicode 字串的指標。

### <a name="return-value"></a>傳回值

不使用返回值。

### <a name="remarks"></a>備註

此成員函數類比[CBEM_SETWINDOWTHEME](/windows/win32/Controls/cbem-setwindowtheme)訊息的功能,如 Windows SDK 中所述。

## <a name="see-also"></a>另請參閱

[MFC 範例 MFCIE](../../overview/visual-cpp-samples.md)<br/>
[CComboBox 類別](../../mfc/reference/ccombobox-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CComboBox 類別](../../mfc/reference/ccombobox-class.md)
