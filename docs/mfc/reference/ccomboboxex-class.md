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
ms.openlocfilehash: d7a39dd19a51bc5bab0f924d360d594bddf89b44
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265934"
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
|[CComboBoxEx::CComboBoxEx](#ccomboboxex)|建構 `CComboBoxEx` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComboBoxEx::Create](#create)|建立下拉式方塊，並將它附加至`CComboBoxEx`物件。|
|[CComboBoxEx::CreateEx](#createex)|建立具有指定的 Windows 延伸樣式的下拉式方塊，並將它附加至`ComboBoxEx`物件。|
|[CComboBoxEx::DeleteItem](#deleteitem)|移除項目從`ComboBoxEx`控制項。|
|[CComboBoxEx::GetComboBoxCtrl](#getcomboboxctrl)|擷取子下拉式方塊控制項的指標。|
|[CComboBoxEx::GetEditCtrl](#geteditctrl)|擷取的編輯控制項部分的控制代碼`ComboBoxEx`控制項。|
|[CComboBoxEx::GetExtendedStyle](#getextendedstyle)|擷取用於延伸的樣式`ComboBoxEx`控制項。|
|[CComboBoxEx::GetImageList](#getimagelist)|擷取映像清單中，指派給指標`ComboBoxEx`控制項。|
|[CComboBoxEx::GetItem](#getitem)|擷取項目資訊指定`ComboBoxEx`項目。|
|[CComboBoxEx::HasEditChanged](#haseditchanged)|判斷使用者是否已變更的內容`ComboBoxEx`鍵入來編輯控制項。|
|[CComboBoxEx::InsertItem](#insertitem)|插入新的項目中`ComboBoxEx`控制項。|
|[CComboBoxEx::SetExtendedStyle](#setextendedstyle)|設定延伸的樣式內`ComboBoxEx`控制項。|
|[CComboBoxEx::SetImageList](#setimagelist)|設定的映像清單`ComboBoxEx`控制項。|
|[CComboBoxEx::SetItem](#setitem)|設定的屬性中的項目`ComboBoxEx`控制項。|
|[CComboBoxEx::SetWindowTheme](#setwindowtheme)|設定之視覺樣式的擴充的下拉式方塊控制項。|

## <a name="remarks"></a>備註

使用`CComboBoxEx`建立下拉式方塊控制項，您不再需要實作您自己的影像繪圖程式碼。 請改用`CComboBoxEx`存取映像，從影像清單。

## <a name="image-list-support"></a>影像清單的支援

在標準下拉式方塊中，下拉式方塊的擁有者負責建立下拉式方塊中的，做為主控描繪控制項繪製影像。 當您使用`CComboBoxEx`，您不需要設定 CBS_OWNERDRAWFIXED 和 CBS_HASSTRINGS 的繪製樣式，因為它們隱含。 否則，您必須撰寫程式碼來執行繪製作業。 A`CComboBoxEx`控制項支援最多三個映像，每個項目： 一個用於已選取的狀態，如未選取狀態，其中一個，一個用於覆疊影像。

## <a name="styles"></a>樣式

`CComboBoxEx` 支援 CBS_SIMPLE、 CBS_DROPDOWN、 CBS_DROPDOWNLIST 和 WS_CHILD 的樣式。 建立視窗時傳遞的所有其他樣式會忽略該控制項。 建立視窗之後，您可以提供其他下拉式方塊樣式藉由呼叫`CComboBoxEx`成員函式[SetExtendedStyle](#setextendedstyle)。 使用這些樣式中，您可以：

- 設定在清單中要區分大小寫的字串搜尋。

- 建立下拉式方塊控制項，會使用斜線 （'/')、 反斜線 ('\\')，和句號 ('。 ') 做為 word 分隔符號的字元。 這允許使用者跳斷字，使用鍵盤快速鍵 CTRL + 方向鍵。

- 設定下拉式方塊控制項來顯示，或不會顯示映像。 如果沒有影像隨即顯示，下拉式方塊可以移除文字縮排可容納映像。

- 建立窄的下拉式方塊控制項，包括讓它裁剪更廣的下拉式方塊包含調整大小。

這些樣式旗標會進一步說明，在[使用 CComboBoxEx](../../mfc/using-ccomboboxex.md)。

## <a name="item-retention-and-callback-item-attributes"></a>保留項目和回呼項目屬性

項目資訊，例如項目和影像、 縮排的值及文字字串的索引會儲存在 Win32 結構[COMBOBOXEXITEM](/windows/desktop/api/commctrl/ns-commctrl-tagcomboboxexitema)、 Windows SDK 中所述。 此結構也包含對應至回呼旗標的成員。

如需詳細的概念性的討論，請參閱[使用 CComboBoxEx](../../mfc/using-ccomboboxex.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CComboBox](../../mfc/reference/ccombobox-class.md)

`CComboBoxEx`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

##  <a name="ccomboboxex"></a>  CComboBoxEx::CComboBoxEx

呼叫此成員函式來建立`CComboBoxEx`物件。

```
CComboBoxEx();
```

##  <a name="create"></a>  CComboBoxEx::Create

建立下拉式方塊，並將它附加至`CComboBoxEx`物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定套用至下拉式方塊的下拉式方塊樣式的組合。 請參閱**備註**如下如需樣式的詳細資訊。

*rect*<br/>
參考[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)結構，也就是位置和下拉式方塊的大小。

*pParentWnd*<br/>
指標[CWnd](../../mfc/reference/cwnd-class.md)物件，為下拉式方塊的父視窗 (通常`CDialog`)。 它必須不是 NULL。

*nID*<br/>
指定下拉式方塊的控制項 id。

### <a name="return-value"></a>傳回值

如果物件已成功; 建立為非零否則為 0。

### <a name="remarks"></a>備註

建立`CComboBoxEx`物件在兩個步驟：

1. 呼叫[CComboBoxEx](#ccomboboxex)建構`CComboBoxEx`物件。

1. 呼叫此成員函式，會建立擴充的 Windows 下拉式方塊，並將它附加至`CComboBoxEx`物件。

當您呼叫`Create`，MFC 初始化的通用控制項。

當您建立下拉式方塊時，您可以指定任何或所有下列下拉式方塊樣式：

- CBS_SIMPLE

- CBS_DROPDOWN

- CBS_DROPDOWNLIST

- CBS_AUTOHSCROLL

- WS_CHILD

建立視窗時傳遞的所有其他樣式會被忽略。 `ComboBoxEx`控制項也支援提供的額外功能的延伸的樣式。 這些樣式所述[ComboBoxEx 控制項延伸的樣式](/windows/desktop/Controls/comboboxex-control-extended-styles)，Windows SDK 中。 藉由呼叫設定這些樣式[SetExtendedStyle](#setextendedstyle)。

如果您想要使用擴充的 windows 樣式和控制項，呼叫[CreateEx](#createex)而不是`Create`。

##  <a name="createex"></a>  CComboBoxEx::CreateEx

呼叫此函式來建立擴充的下拉式方塊控制項 （子視窗） 和其關聯`CComboBoxEx`物件。

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
指定正在建立之控制項的延伸的樣式。 如需延伸的 Windows 樣式的清單，請參閱 < *dwExStyle*參數[CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) Windows SDK 中。

*dwStyle*<br/>
下拉式方塊控制項的樣式。 請參閱[建立](#create)如需樣式的清單。

*rect*<br/>
參考[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)結構描述的大小和位置，在中建立工作區座標中的視窗*pParentWnd*。

*pParentWnd*<br/>
是控制項的父視窗的指標。

*nID*<br/>
控制項的子視窗識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

使用`CreateEx`而非`Create`套用延伸的 Windows 樣式，由 Windows 延伸的樣式前置詞**WS_EX_**。

`CreateEx` 建立具有所指定的擴充 Windows 樣式的控制項*dwExStyle*。 您必須將延伸的樣式特定擴充的下拉式方塊控制項中，使用[SetExtendedStyle](#setextendedstyle)。 例如，使用`CreateEx`將這類樣式設定為 WS_EX_CONTEXTHELP，但使用`SetExtendedStyle`將這類樣式設定為 CBES_EX_CASESENSITIVE。 如需詳細資訊，請參閱本主題中所述的樣式[ComboBoxEx 控制項擴充樣式](/windows/desktop/Controls/comboboxex-control-extended-styles)Windows SDK 中。

##  <a name="deleteitem"></a>  CComboBoxEx::DeleteItem

移除項目從`ComboBoxEx`控制項。

```
int DeleteItem(int iIndex);
```

### <a name="parameters"></a>參數

*iIndex*<br/>
要移除之項目的以零為起始的索引。

### <a name="return-value"></a>傳回值

控制項中所剩餘的項目數目。 如果*iIndex*是無效的則函數會傳回 CB_ERR。

### <a name="remarks"></a>備註

此成員函式實作的訊息功能[CBEM_DELETEITEM](/windows/desktop/Controls/cbem-deleteitem)、 Windows SDK 中所述。 當您呼叫 DeleteItem [WM_NOTIFY](/windows/desktop/controls/wm-notify) CBEN_DELETEITEM 通知訊息會傳送至父視窗。

##  <a name="getcomboboxctrl"></a>  CComboBoxEx::GetComboBoxCtrl

呼叫此成員函式中的下拉式方塊控制項中取得的指標`CComboBoxEx`物件。

```
CComboBox* GetComboBoxCtrl();
```

### <a name="return-value"></a>傳回值

`CComboBox` 物件的指標。

### <a name="remarks"></a>備註

`CComboBoxEx`控制項包含封裝的父視窗的`CComboBox`。

`CComboBox`傳回的值所指向的物件是暫存物件，並在下一步 的閒置處理期間終結。

##  <a name="geteditctrl"></a>  CComboBoxEx::GetEditCtrl

呼叫此成員函式來取得編輯控制項下拉式方塊的指標。

```
CEdit* GetEditCtrl();
```

### <a name="return-value"></a>傳回值

指標[CEdit](../../mfc/reference/cedit-class.md)物件。

### <a name="remarks"></a>備註

A `CComboBoxEx` CBS_DROPDOWN 樣式建立時，控制項使用的編輯方塊。

`CEdit`傳回的值所指向的物件是暫存物件，並在下一步 的閒置處理期間終結。

##  <a name="getextendedstyle"></a>  CComboBoxEx::GetExtendedStyle

呼叫此成員函式，以取得所使用的擴充的樣式`CComboBoxEx`控制項。

```
DWORD GetExtendedStyle() const;
```

### <a name="return-value"></a>傳回值

包含用於下拉式方塊控制項的擴充的樣式 DWORD 值。

### <a name="remarks"></a>備註

請參閱[ComboBoxEx 控制項擴充樣式](/windows/desktop/Controls/comboboxex-control-extended-styles)這些樣式的詳細資訊的 Windows SDK 中。

##  <a name="getimagelist"></a>  CComboBoxEx::GetImageList

呼叫此成員函式，以取得所使用的影像清單的指標`CComboBoxEx`控制項。

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>傳回值

指標[CImageList](../../mfc/reference/cimagelist-class.md)物件。 如果失敗，此成員函式會傳回 NULL。

### <a name="remarks"></a>備註

`CImageList`傳回的值所指向的物件是暫存物件，並在下一步 的閒置處理期間終結。

##  <a name="getitem"></a>  CComboBoxEx::GetItem

擷取項目資訊指定`ComboBoxEx`項目。

```
BOOL GetItem(COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>參數

*pCBItem*<br/>
指標[COMBOBOXEXITEM](/windows/desktop/api/commctrl/ns-commctrl-tagcomboboxexitema)結構，將會收到項目資訊。

### <a name="return-value"></a>傳回值

如果作業成功，為非零否則為 0。

### <a name="remarks"></a>備註

此成員函式實作的訊息功能[CBEM_GETITEM](/windows/desktop/Controls/cbem-getitem)、 Windows SDK 中所述。

##  <a name="haseditchanged"></a>  CComboBoxEx::HasEditChanged

判斷使用者是否已變更的內容`ComboBoxEx`鍵入來編輯控制項。

```
BOOL HasEditChanged();
```

### <a name="return-value"></a>傳回值

如果使用者在控制項的編輯方塊中，輸入了非零值否則為 0。

### <a name="remarks"></a>備註

此成員函式實作的訊息功能[CBEM_HASEDITCHANGED](/windows/desktop/Controls/cbem-haseditchanged)、 Windows SDK 中所述。

##  <a name="insertitem"></a>  CComboBoxEx::InsertItem

插入新的項目中`ComboBoxEx`控制項。

```
int InsertItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>參數

*pCBItem*<br/>
指標[COMBOBOXEXITEM](/windows/desktop/api/commctrl/ns-commctrl-tagcomboboxexitema)結構，將會收到項目資訊。 此結構包含之項目的回呼旗標值。

### <a name="return-value"></a>傳回值

新的項目插入成功; 如果索引否則為-1。

### <a name="remarks"></a>備註

當您呼叫`InsertItem`，則[WM_NOTIFY](/windows/desktop/controls/wm-notify)訊息，其[CBEN_INSERTITEM](/windows/desktop/Controls/cben-insertitem)通知會傳送至父視窗。

##  <a name="setextendedstyle"></a>  CComboBoxEx::SetExtendedStyle

呼叫此成員函式來設定延伸用於擴充控制項的下拉式方塊的樣式。

```
DWORD SetExtendedStyle(
    DWORD dwExMask,
    DWORD dwExStyles);
```

### <a name="parameters"></a>參數

*dwExMask*<br/>
DWORD 值，指出在哪些樣式*dwExStyles*會受到影響。 只有在延伸的樣式*dwExMask*將會變更。 因為，仍會維護所有其他樣式。 如果此參數為零，則所有的樣式*dwExStyles*會受到影響。

*dwExStyles*<br/>
DWORD 值，包含下拉式方塊控制項的延伸來設定控制項的樣式。

### <a name="return-value"></a>傳回值

包含先前用於控制項的擴充的樣式 DWORD 值。

### <a name="remarks"></a>備註

請參閱[ComboBoxEx 控制項擴充樣式](/windows/desktop/Controls/comboboxex-control-extended-styles)這些樣式的詳細資訊的 Windows SDK 中。

若要建立擴充控制項具有延伸的 windows 樣式的下拉式方塊，請使用[CreateEx](#createex)。

##  <a name="setimagelist"></a>  CComboBoxEx::SetImageList

設定的映像清單`ComboBoxEx`控制項。

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>參數

*pImageList*<br/>
指標`CImageList`物件，其中包含要搭配使用的影像`CComboBoxEx`控制項。

### <a name="return-value"></a>傳回值

指標[CImageList](../../mfc/reference/cimagelist-class.md)物件，其中包含先前所使用的影像`CComboBoxEx`控制項。 如果先前已經不設定任何映像清單，則為 NULL。

### <a name="remarks"></a>備註

此成員函式實作的訊息功能[CBEM_SETIMAGELIST](/windows/desktop/Controls/cbem-setimagelist)、 Windows SDK 中所述。 如果您變更預設編輯控制項的高度，呼叫 Win32 函式[SetWindowPos](/windows/desktop/api/winuser/nf-winuser-setwindowpos)調整您的控制項的大小之後您呼叫, `SetImageList`，或無法正常顯示。

`CImageList`傳回的值所指向的物件是暫存物件，並在下一步 的閒置處理期間終結。

##  <a name="setitem"></a>  CComboBoxEx::SetItem

設定的屬性中的項目`ComboBoxEx`控制項。

```
BOOL SetItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>參數

*pCBItem*<br/>
指標[COMBOBOXEXITEM](/windows/desktop/api/commctrl/ns-commctrl-tagcomboboxexitema)結構，將會收到項目資訊。

### <a name="return-value"></a>傳回值

如果作業成功，為非零否則為 0。

### <a name="remarks"></a>備註

此成員函式實作的訊息功能[CBEM_SETITEM](/windows/desktop/Controls/cbem-setitem)、 Windows SDK 中所述。

##  <a name="setwindowtheme"></a>  CComboBoxEx::SetWindowTheme

設定之視覺樣式的擴充的下拉式方塊控制項。

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>參數

*pszSubAppName*<br/>
包含擴充的下拉式方塊視覺化樣式，若要設定的 Unicode 字串指標。

### <a name="return-value"></a>傳回值

不會使用傳回的值。

### <a name="remarks"></a>備註

此成員函式會模擬[CBEM_SETWINDOWTHEME](/windows/desktop/Controls/cbem-setwindowtheme)訊息、 Windows SDK 中所述。

## <a name="see-also"></a>另請參閱

[MFC 範例 MFCIE](../../visual-cpp-samples.md)<br/>
[CComboBox 類別](../../mfc/reference/ccombobox-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CComboBox 類別](../../mfc/reference/ccombobox-class.md)
