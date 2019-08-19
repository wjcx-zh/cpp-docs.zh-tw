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
ms.openlocfilehash: 7d46f175a62cda7f1ff08327830f1dffe2967727
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507173"
---
# <a name="ccomboboxex-class"></a>CComboBoxEx 類別

藉由提供影像清單的支援，擴充下拉式方塊控制項。

## <a name="syntax"></a>語法

```
class CComboBoxEx : public CComboBox
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CComboBoxEx::CComboBoxEx](#ccomboboxex)|建構 `CComboBoxEx` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComboBoxEx::Create](#create)|建立下拉式方塊, 並將其附加至`CComboBoxEx`物件。|
|[CComboBoxEx::CreateEx](#createex)|建立具有指定之 Windows 擴充樣式的下拉式方塊, 並將其附加`ComboBoxEx`至物件。|
|[CComboBoxEx::DeleteItem](#deleteitem)|從`ComboBoxEx`控制項移除專案。|
|[CComboBoxEx::GetComboBoxCtrl](#getcomboboxctrl)|抓取子下拉式方塊控制項的指標。|
|[CComboBoxEx::GetEditCtrl](#geteditctrl)|抓取`ComboBoxEx`控制項之編輯控制項部分的控制碼。|
|[CComboBoxEx::GetExtendedStyle](#getextendedstyle)|抓取`ComboBoxEx`控制項使用的延伸樣式。|
|[CComboBoxEx::GetImageList](#getimagelist)|抓取指派`ComboBoxEx`給控制項之影像清單的指標。|
|[CComboBoxEx::GetItem](#getitem)|抓取指定`ComboBoxEx`專案的專案資訊。|
|[CComboBoxEx::HasEditChanged](#haseditchanged)|藉由輸入, 判斷使用者是否已變更`ComboBoxEx`編輯控制項的內容。|
|[CComboBoxEx::InsertItem](#insertitem)|在`ComboBoxEx`控制項中插入新專案。|
|[CComboBoxEx::SetExtendedStyle](#setextendedstyle)|設定控制項內的`ComboBoxEx`擴充樣式。|
|[CComboBoxEx::SetImageList](#setimagelist)|設定`ComboBoxEx`控制項的影像清單。|
|[CComboBoxEx::SetItem](#setitem)|設定`ComboBoxEx`控制項中專案的屬性。|
|[CComboBoxEx::SetWindowTheme](#setwindowtheme)|設定擴充下拉式方塊控制項的視覺化樣式。|

## <a name="remarks"></a>備註

藉由`CComboBoxEx`使用建立下拉式方塊控制項, 您就不再需要執行自己的影像繪圖程式碼。 相反地, `CComboBoxEx`請使用來存取影像清單中的影像。

## <a name="image-list-support"></a>影像清單支援

在標準下拉式方塊中, 下拉式方塊的擁有者會藉由建立下拉式列示方塊作為主控描繪控制項, 負責繪製影像。 當您使用`CComboBoxEx`時, 您不需要設定繪製樣式 CBS_OWNERDRAWFIXED 和 CBS_HASSTRINGS, 因為它們是隱含的。 否則, 您必須撰寫程式碼來執行繪製作業。 `CComboBoxEx`控制項支援每個專案最多三個影像: 一個用於選取的狀態, 一個用於未選取的狀態, 另一個用於重迭影像。

## <a name="styles"></a>樣式

`CComboBoxEx`支援 CBS_SIMPLE、CBS_DROPDOWN、CBS_DROPDOWNLIST 和 WS_CHILD 樣式。 當您建立視窗時所傳遞的其他所有樣式, 都是由控制項忽略。 建立視窗之後, 您可以藉由呼叫`CComboBoxEx`成員函式[SetExtendedStyle](#setextendedstyle)來提供其他下拉式列示方塊樣式。 使用這些樣式, 您可以:

- 將清單中的字串搜尋設定為區分大小寫。

- 建立下拉式方塊控制項, 以使用斜線 ('/')、反斜線 ('\\') 和句點 ('. ') 字元做為文字分隔符號。 這可讓使用者使用鍵盤快速鍵 CTRL + 箭號, 從 word 跳到 word。

- 將下拉式方塊控制項設定為 [顯示] 或 [不顯示影像]。 如果沒有顯示任何影像, 下拉式方塊可以移除容納影像的文字縮排。

- 建立窄的下拉式方塊控制項, 包括調整其大小, 使其裁剪其所包含的較寬下拉式方塊。

這些樣式旗標會在[使用 CComboBoxEx](../../mfc/using-ccomboboxex.md)中進一步說明。

## <a name="item-retention-and-callback-item-attributes"></a>專案保留和回呼專案屬性

專案資訊 (例如專案和影像的索引、縮排值和文字字串) 會儲存在 Win32 結構[COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw)中, 如 Windows SDK 中所述。 結構也包含對應至回呼旗標的成員。

如需詳細的概念性討論, 請參閱[使用 CComboBoxEx](../../mfc/using-ccomboboxex.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CComboBox](../../mfc/reference/ccombobox-class.md)

`CComboBoxEx`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

##  <a name="ccomboboxex"></a>CComboBoxEx:: CComboBoxEx

呼叫這個成員函式以建立`CComboBoxEx`物件。

```
CComboBoxEx();
```

##  <a name="create"></a>CComboBoxEx:: Create

建立下拉式方塊, 並將其附加至`CComboBoxEx`物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定套用至下拉式方塊之下拉式列示方塊樣式的組合。 如需樣式的詳細資訊, 請參閱下面的**備註**。

*rect*<br/>
[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](/previous-versions/dd162897\(v=vs.85\))結構的參考, 這是下拉式方塊的位置和大小。

*pParentWnd*<br/>
[CWnd](../../mfc/reference/cwnd-class.md)物件的指標, 這是下拉式方塊的父視窗 (通常是`CDialog`)。 不得為 Null。

*nID*<br/>
指定下拉式方塊的控制項識別碼。

### <a name="return-value"></a>傳回值

如果成功建立物件, 則為非零;否則為0。

### <a name="remarks"></a>備註

以兩個步驟建立物件:`CComboBoxEx`

1. 呼叫[CComboBoxEx](#ccomboboxex)來建立`CComboBoxEx`物件。

1. 呼叫這個成員函式, 它會建立擴充的 Windows 下拉式方塊, 並將`CComboBoxEx`其附加至物件。

當您呼叫`Create`時, MFC 會初始化通用控制項。

當您建立下拉式方塊時, 可以指定下列任何一個或所有的下拉式方塊樣式:

- CBS_SIMPLE

- CBS_DROPDOWN

- CBS_DROPDOWNLIST

- CBS_AUTOHSCROLL

- WS_CHILD

當您建立視窗時所傳遞的其他所有樣式都會被忽略。 `ComboBoxEx`控制項也支援提供額外功能的擴充樣式。 這些樣式在 Windows SDK 中是以[ComboBoxEx 控制項擴充樣式](/windows/win32/Controls/comboboxex-control-extended-styles)來說明。 藉由呼叫[SetExtendedStyle](#setextendedstyle)來設定這些樣式。

如果您想要搭配控制項使用擴充的 windows 樣式, 請呼叫[CreateEx](#createex) , `Create`而不是。

##  <a name="createex"></a>CComboBoxEx:: CreateEx

呼叫此函式可建立擴充的下拉式方塊控制項 (子視窗), 並將它與`CComboBoxEx`物件產生關聯。

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
指定所要建立之控制項的延伸樣式。 如需擴充 Windows 樣式的清單, 請參閱 Windows SDK 中[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*參數。

*dwStyle*<br/>
下拉式方塊控制項的樣式。 如需樣式清單, 請參閱[建立](#create)。

*rect*<br/>
[矩形](/previous-versions/dd162897\(v=vs.85\))結構的參考, 描述要建立之視窗的大小和位置, 以*pParentWnd*的用戶端座標表示。

*pParentWnd*<br/>
做為控制項父系之視窗的指標。

*nID*<br/>
控制項的子視窗識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

使用`CreateEx`而非來套用擴充的 windows 樣式 (由 Windows 擴充樣式指定于 WS_EX_ 的前面) `Create` 。

`CreateEx`使用*dwExStyle*所指定的擴充 Windows 樣式來建立控制項。 您必須使用[SetExtendedStyle](#setextendedstyle)來設定擴充下拉式方塊控制項特定的擴充樣式。 例如, 使用`CreateEx`將這類樣式設定為 WS_EX_CONTEXTHELP, 但使用`SetExtendedStyle`來將這類樣式設定為 CBES_EX_CASESENSITIVE。 如需詳細資訊, 請參閱 Windows SDK 中的[控制項擴充樣式](/windows/win32/Controls/comboboxex-control-extended-styles)主題中所述的樣式。

##  <a name="deleteitem"></a>CComboBoxEx::D eleteItem

從`ComboBoxEx`控制項移除專案。

```
int DeleteItem(int iIndex);
```

### <a name="parameters"></a>參數

*iIndex*<br/>
要移除之專案的以零為基底的索引。

### <a name="return-value"></a>傳回值

控制項中剩餘的專案數。 如果*iIndex*無效, 函數會傳回 CB_ERR。

### <a name="remarks"></a>備註

此成員函式會執行 message [CBEM_DELETEITEM](/windows/win32/Controls/cbem-deleteitem)的功能, 如 Windows SDK 中所述。 當您呼叫 DeleteItem 時, 會將具有 CBEN_DELETEITEM 通知的[WM_NOTIFY](/windows/win32/controls/wm-notify)訊息傳送至父視窗。

##  <a name="getcomboboxctrl"></a>  CComboBoxEx::GetComboBoxCtrl

呼叫這個成員函式可取得`CComboBoxEx`物件內下拉式方塊控制項的指標。

```
CComboBox* GetComboBoxCtrl();
```

### <a name="return-value"></a>傳回值

          `CComboBox` 物件的指標。

### <a name="remarks"></a>備註

控制項是由父視窗組成, 其會`CComboBox`封裝。 `CComboBoxEx`

傳回`CComboBox`值所指向的物件是暫存物件, 並在下一個空閒處理時間終結。

##  <a name="geteditctrl"></a>  CComboBoxEx::GetEditCtrl

呼叫這個成員函式, 以取得下拉式方塊編輯控制項的指標。

```
CEdit* GetEditCtrl();
```

### <a name="return-value"></a>傳回值

[CEdit](../../mfc/reference/cedit-class.md)物件的指標。

### <a name="remarks"></a>備註

當使用 CBS_DROPDOWN 樣式建立控制項時,控制項會使用編輯方塊。`CComboBoxEx`

傳回`CEdit`值所指向的物件是暫存物件, 並在下一個空閒處理時間終結。

##  <a name="getextendedstyle"></a>CComboBoxEx:: GetExtendedStyle

呼叫這個成員函式, 以取得用於`CComboBoxEx`控制項的延伸樣式。

```
DWORD GetExtendedStyle() const;
```

### <a name="return-value"></a>傳回值

DWORD 值, 其中包含用於下拉式方塊控制項的延伸樣式。

### <a name="remarks"></a>備註

如需這些樣式的詳細資訊, 請參閱 Windows SDK 中的[ComboBoxEx 控制項擴充樣式](/windows/win32/Controls/comboboxex-control-extended-styles)。

##  <a name="getimagelist"></a>CComboBoxEx:: GetImageList

呼叫這個成員函式, 以取得`CComboBoxEx`控制項所使用影像清單的指標。

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>傳回值

[CImageList](../../mfc/reference/cimagelist-class.md)物件的指標。 如果失敗, 此成員函式會傳回 Null。

### <a name="remarks"></a>備註

傳回`CImageList`值所指向的物件是暫存物件, 並在下一個空閒處理時間終結。

##  <a name="getitem"></a>CComboBoxEx:: GetItem

抓取指定`ComboBoxEx`專案的專案資訊。

```
BOOL GetItem(COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>參數

*pCBItem*<br/>
將接收專案資訊之[COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw)結構的指標。

### <a name="return-value"></a>傳回值

如果作業成功, 則為非零;否則為0。

### <a name="remarks"></a>備註

此成員函式會執行 message [CBEM_GETITEM](/windows/win32/Controls/cbem-getitem)的功能, 如 Windows SDK 中所述。

##  <a name="haseditchanged"></a>CComboBoxEx:: HasEditChanged

藉由輸入, 判斷使用者是否已變更`ComboBoxEx`編輯控制項的內容。

```
BOOL HasEditChanged();
```

### <a name="return-value"></a>傳回值

如果使用者已在控制項的編輯方塊中輸入, 則為非零值;否則為0。

### <a name="remarks"></a>備註

此成員函式會執行 message [CBEM_HASEDITCHANGED](/windows/win32/Controls/cbem-haseditchanged)的功能, 如 Windows SDK 中所述。

##  <a name="insertitem"></a>CComboBoxEx:: InsertItem

在`ComboBoxEx`控制項中插入新專案。

```
int InsertItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>參數

*pCBItem*<br/>
將接收專案資訊之[COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw)結構的指標。 此結構包含專案的回呼旗標值。

### <a name="return-value"></a>傳回值

插入新專案的索引 (如果成功);否則為-1。

### <a name="remarks"></a>備註

當您呼叫`InsertItem`時, 會將具有[CBEN_INSERTITEM](/windows/win32/Controls/cben-insertitem)通知的[WM_NOTIFY](/windows/win32/controls/wm-notify)訊息傳送至父視窗。

##  <a name="setextendedstyle"></a>CComboBoxEx:: SetExtendedStyle

呼叫這個成員函式, 以設定用於下拉式方塊擴充控制項的延伸樣式。

```
DWORD SetExtendedStyle(
    DWORD dwExMask,
    DWORD dwExStyles);
```

### <a name="parameters"></a>參數

*dwExMask*<br/>
DWORD 值, 指出要影響*dwExStyles*中的哪一種樣式。 只有*dwExMask*中的擴充樣式才會變更。 所有其他樣式將會維持不變。 如果此參數為零, 則*dwExStyles*中的所有樣式都會受到影響。

*dwExStyles*<br/>
DWORD 值, 其中包含要為控制項設定的下拉式方塊控制項擴充樣式。

### <a name="return-value"></a>傳回值

DWORD 值, 其中包含先前用於控制項的延伸樣式。

### <a name="remarks"></a>備註

如需這些樣式的詳細資訊, 請參閱 Windows SDK 中的[ComboBoxEx 控制項擴充樣式](/windows/win32/Controls/comboboxex-control-extended-styles)。

若要建立具有擴充 windows 樣式的下拉式方塊擴充控制項, 請使用[CreateEx](#createex)。

##  <a name="setimagelist"></a>CComboBoxEx:: SetImageList

設定`ComboBoxEx`控制項的影像清單。

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>參數

*pImageList*<br/>
`CImageList`物件的指標, 其中包含要`CComboBoxEx`與控制項搭配使用的影像。

### <a name="return-value"></a>傳回值

[CImageList](../../mfc/reference/cimagelist-class.md)物件的指標, 其中包含`CComboBoxEx`控制項先前使用的影像。 如果先前未設定影像清單, 則為 Null。

### <a name="remarks"></a>備註

此成員函式會執行 message [CBEM_SETIMAGELIST](/windows/win32/Controls/cbem-setimagelist)的功能, 如 Windows SDK 中所述。 如果您變更預設編輯控制項的高度, 請在呼叫`SetImageList`之後呼叫 Win32 函式[SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos)來調整控制項的大小, 否則將無法正確顯示。

傳回`CImageList`值所指向的物件是暫存物件, 並在下一個空閒處理時間終結。

##  <a name="setitem"></a>CComboBoxEx:: SetItem

設定`ComboBoxEx`控制項中專案的屬性。

```
BOOL SetItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>參數

*pCBItem*<br/>
將接收專案資訊之[COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw)結構的指標。

### <a name="return-value"></a>傳回值

如果作業成功, 則為非零;否則為0。

### <a name="remarks"></a>備註

此成員函式會執行 message [CBEM_SETITEM](/windows/win32/Controls/cbem-setitem)的功能, 如 Windows SDK 中所述。

##  <a name="setwindowtheme"></a>CComboBoxEx:: SetWindowTheme

設定擴充下拉式方塊控制項的視覺化樣式。

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>參數

*pszSubAppName*<br/>
Unicode 字串的指標, 其中包含要設定的擴充下拉式列示方塊視覺樣式。

### <a name="return-value"></a>傳回值

不使用傳回值。

### <a name="remarks"></a>備註

此成員函式會模擬[CBEM_SETWINDOWTHEME](/windows/win32/Controls/cbem-setwindowtheme)訊息的功能, 如 Windows SDK 中所述。

## <a name="see-also"></a>另請參閱

[MFC 範例 MFCIE](../../overview/visual-cpp-samples.md)<br/>
[CComboBox 類別](../../mfc/reference/ccombobox-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CComboBox 類別](../../mfc/reference/ccombobox-class.md)
