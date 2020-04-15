---
title: CMFCRibbonComboBox 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::AddItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::DeleteItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::EnableDropDownListResize
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::FindItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetCount
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetCurSel
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetDropDownHeight
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetIntermediateSize
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetItemData
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::HasEditBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::IsResizeDropDownList
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::OnSelectItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::RemoveAllItems
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::SelectItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::SetDropDownHeight
helpviewer_keywords:
- CMFCRibbonComboBox [MFC], CMFCRibbonComboBox
- CMFCRibbonComboBox [MFC], AddItem
- CMFCRibbonComboBox [MFC], DeleteItem
- CMFCRibbonComboBox [MFC], EnableDropDownListResize
- CMFCRibbonComboBox [MFC], FindItem
- CMFCRibbonComboBox [MFC], GetCount
- CMFCRibbonComboBox [MFC], GetCurSel
- CMFCRibbonComboBox [MFC], GetDropDownHeight
- CMFCRibbonComboBox [MFC], GetIntermediateSize
- CMFCRibbonComboBox [MFC], GetItem
- CMFCRibbonComboBox [MFC], GetItemData
- CMFCRibbonComboBox [MFC], HasEditBox
- CMFCRibbonComboBox [MFC], IsResizeDropDownList
- CMFCRibbonComboBox [MFC], OnSelectItem
- CMFCRibbonComboBox [MFC], RemoveAllItems
- CMFCRibbonComboBox [MFC], SelectItem
- CMFCRibbonComboBox [MFC], SetDropDownHeight
ms.assetid: 9b29a6a4-cf17-4152-9b13-0bf90784b30d
ms.openlocfilehash: 5846b1c5590a756f0a0820583af3d0b159968ea2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375232"
---
# <a name="cmfcribboncombobox-class"></a>CMFCRibbonComboBox 類別

類`CMFCRibbonComboBox`實現組合框控件,您可以將該控件添加到功能區列、功能區面板或功能區彈出功能表中。

## <a name="syntax"></a>語法

```cpp
class CMFCRibbonComboBox : public CMFCRibbonEdit
```

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|名稱|描述|
|----------|-----------------|
|[CMFC 剪彩組合盒:CMFC 剪綵組合盒](#cmfcribboncombobox)|構造 CMFC 功能組合博博盒物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFC 功能組合Box:新增專案](#additem)|將唯一專案追加到清單框。|
|[CMFC功能中心盒::Delete專案](#deleteitem)|從清單框中刪除指定的專案。|
|[CMFC 功能組合Box::啟用下拉列表重新調整大小](#enabledropdownlistresize)|指定清單框在下垂時是否可以更改大小。|
|[CMFC 功能通訊包::尋找專案](#finditem)|返回清單框中與指定字串匹配的第一項的索引。|
|[CMFC 功能放大縮小字型功能 放大縮小字型功能](#getcount)|傳回清單框中的項目數。|
|[CMFC 功能放大縮小字型功能 放大縮小字型功能](#getcursel)|在清單框中獲取當前選定項的索引。|
|[CMFC 功能通信框::獲取下降高度](#getdropdownheight)|下下列表框時獲取清單框的高度。|
|[CMFC 功能組合Box:取得中間尺寸](#getintermediatesize)|返回在中間模式下顯示的組合框的大小。|
|[CMFC 功能通訊包:取得項目](#getitem)|傳回與清單框中指定索引處的項目關聯的字串。|
|[CMFC 功能通訊包:取得項目資料](#getitemdata)|返回與列表框中指定索引處的項關聯的數據。|
|[CMFC功能組合框::已編輯盒](#haseditbox)|指示控制項是否包含編輯框。|
|[CMFC 功能通訊框:重新調整下拉清單](#isresizedropdownlist)|指示清單框是否可以調整大小。|
|[CMFC 功能組合框::在選擇項目上](#onselectitem)|當使用者在清單框中選擇項時,由框架調用。|
|[CMFC 功能組合框::刪除所有專案](#removeallitems)|從清單框中刪除所有專案並清除編輯框。|
|[CMFC 功能組合框::選擇項目](#selectitem)|在清單框中選擇專案。|
|[CMFC 功能組合Box::設定下拉高度](#setdropdownheight)|下下列表框時設置其高度。|

## <a name="remarks"></a>備註

功能區組合框由列表框與用戶可以編輯的靜態標籤或標籤組合而成。 建立功能區組合框時,必須指定所需的類型。

## <a name="example"></a>範例

下面的範例展示如何建構`CMFCRibbonComboBox`類的物件、將項添加到組合框中、在組合框中選擇項以及向面板添加組合框。

[!code-cpp[NVC_MFC_RibbonApp#11](../../mfc/reference/codesnippet/cpp/cmfcribboncombobox-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)

[CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)

## <a name="requirements"></a>需求

**標題:** afxribboncombox.h

## <a name="cmfcribboncomboboxadditem"></a><a name="additem"></a>CMFC 功能組合Box:新增專案

將唯一專案追加到清單框。

```cpp
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>參數

*lpszItem*<br/>
[在]要添加的項的字串。

*dwData*<br/>
[在]與要添加的項關聯的數據。

### <a name="return-value"></a>傳回值

附加項的零基索引。

## <a name="cmfcribboncomboboxcmfcribboncombobox"></a><a name="cmfcribboncombobox"></a>CMFC 剪彩組合盒:CMFC 剪綵組合盒

建構 `CMFCRibbonComboBox` 物件。

```cpp
public:
CMFCRibbonComboBox(
    UINT nID,
    BOOL bHasEditBox=TRUE,
    Int nWidth=-1,
    LPCTSTR lpszLabel=NULL,
    Int nImage=-1);

protected:
CMFCRibbonComboBox();
```

### <a name="parameters"></a>參數

*nID*<br/>
[在]組合框的識別碼。

*bHasEditBox*<br/>
[在]如果希望在控制項中使用編輯框,則為 TRUE;否則。

*n 寬度*<br/>
[在]組合框的寬度(以像素為單位);或 -1 表示預設寬度。

*lpszLabel*<br/>
[在]組合框的顯示標籤。

*n 影像*<br/>
[在]組合框的小圖像索引。

### <a name="remarks"></a>備註

默認寬度為 108 圖元。

## <a name="cmfcribboncomboboxdeleteitem"></a><a name="deleteitem"></a>CMFC功能中心盒::Delete專案

從清單框中刪除指定的專案。

```cpp
BOOL DeleteItem(int iIndex);
BOOL DeleteItem(DWORD_PTR dwData);

BOOL DeleteItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>參數

*iIndex*<br/>
[在]要刪除的項的零基索引。

*dwData*<br/>
[在]與要刪除的項關聯的數據。

*lpszText*<br/>
[在]要刪除的項目的字串。 如果有多個具有相同字串的項,則刪除第一個項。

### <a name="return-value"></a>傳回值

如果指定的項已被刪除,則為 TRUE;如果指定專案已被刪除,則為 TRUE。否則,FALSE。

### <a name="remarks"></a>備註

## <a name="cmfcribboncomboboxenabledropdownlistresize"></a><a name="enabledropdownlistresize"></a>CMFC 功能組合Box::啟用下拉列表重新調整大小

指定清單框在下垂時是否可以更改大小。

```cpp
void EnableDropDownListResize(BOOL bEnable=FALSE);
```

### <a name="parameters"></a>參數

*b 啟用*<br/>
[在]TRUE 以啟用大小調整;FALSE 以禁用調整大小。

### <a name="remarks"></a>備註

啟用調整大小後,清單框將更改大小以適合其顯示的專案。

## <a name="cmfcribboncomboboxfinditem"></a><a name="finditem"></a>CMFC 功能通訊包::尋找專案

返回清單框中與指定字串匹配的第一項的索引。

```cpp
int FindItem(LPCTSTR lpszText) const;
```

### <a name="parameters"></a>參數

*lpszText*<br/>
[在]清單框中項目的字串。

### <a name="return-value"></a>傳回值

項的零基索引;或 -1,如果找不到該專案。

### <a name="remarks"></a>備註

## <a name="cmfcribboncomboboxgetcount"></a><a name="getcount"></a>CMFC 功能放大縮小字型功能 放大縮小字型功能

傳回清單框中的項目數。

```cpp
INT_PTR GetCount() const;
```

### <a name="return-value"></a>傳回值

如果清單框不包含任何項,則列表框中的項目數為 0。

### <a name="remarks"></a>備註

## <a name="cmfcribboncomboboxgetcursel"></a><a name="getcursel"></a>CMFC 功能放大縮小字型功能 放大縮小字型功能

在清單框中獲取當前選定項的索引。

```cpp
int GetCurSel() const;
```

### <a name="return-value"></a>傳回值

清單框中選取的零基索引;或 -1,如果未選擇專案。

## <a name="cmfcribboncomboboxgetdropdownheight"></a><a name="getdropdownheight"></a>CMFC 功能通信框::獲取下降高度

下下列表框時獲取清單框的高度。

```cpp
int GetDropDownHeight();
```

### <a name="return-value"></a>傳回值

清單框的高度(以像素為單位)。

### <a name="remarks"></a>備註

## <a name="cmfcribboncomboboxgetintermediatesize"></a><a name="getintermediatesize"></a>CMFC 功能組合Box:取得中間尺寸

返回在中間模式下顯示的組合框的大小。

```cpp
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向組合框的設備上下文。

### <a name="return-value"></a>傳回值

組合框的大小。

### <a name="remarks"></a>備註

返回的大小基於組合框顯示小圖像時的大小。

## <a name="cmfcribboncomboboxgetitem"></a><a name="getitem"></a>CMFC 功能通訊包:取得項目

傳回與清單框中指定索引處的項目關聯的字串。

```cpp
LPCTSTR GetItem(int iIndex) const;
```

### <a name="parameters"></a>參數

*iIndex*<br/>
[在]清單框中項的零基索引。

### <a name="return-value"></a>傳回值

指向與項關聯的字串的指標;否則,如果索引參數無效,或者索引參數為 -1,並且組合框中未選擇任何項,則 NULL。

### <a name="remarks"></a>備註

## <a name="cmfcribboncomboboxgetitemdata"></a><a name="getitemdata"></a>CMFC 功能通訊包:取得項目資料

返回與列表框中指定索引處的項關聯的數據。

```cpp
DWORD_PTR GetItemData(int iIndex) const;
```

### <a name="parameters"></a>參數

*iIndex*<br/>
[在]清單框中項的零基索引。

### <a name="return-value"></a>傳回值

與項關聯的數據;如果項不存在,或者索引參數為 -1,並且列表框中沒有選定項,則為 0。

## <a name="cmfcribboncomboboxhaseditbox"></a><a name="haseditbox"></a>CMFC功能組合框::已編輯盒

指示控制項是否包含編輯框。

```cpp
BOOL HasEditBox() const;
```

### <a name="return-value"></a>傳回值

如果控件包含編輯框,則為 TRUE;如果控件包含編輯框。"否則,FALSE。

### <a name="remarks"></a>備註

## <a name="cmfcribboncomboboxisresizedropdownlist"></a><a name="isresizedropdownlist"></a>CMFC 功能通訊框:重新調整下拉清單

指示清單框是否可以調整大小。

```cpp
BOOL IsResizeDropDownList() const;
```

### <a name="return-value"></a>傳回值

如果清單框可以調整大小,則為 TRUE;否則 FALSE。 [CMFC 功能組合Box::啟用下拉列表重新調整大小](#enabledropdownlistresize)

### <a name="remarks"></a>備註

您可以使用[CMFC 功能區 ComboBox::啟用下拉清單重新調整大小](#enabledropdownlistresize)的方法啟用列表框調整大小。

## <a name="cmfcribboncomboboxonselectitem"></a><a name="onselectitem"></a>CMFC 功能組合框::在選擇項目上

當使用者在清單框中選擇項時,由框架調用。

```cpp
virtual void OnSelectItem(int nItem);
```

### <a name="parameters"></a>參數

*nItem*<br/>
[在]所選項的索引。

### <a name="remarks"></a>備註

如果要處理使用者輸入選擇,則重寫此方法。

## <a name="cmfcribboncomboboxremoveallitems"></a><a name="removeallitems"></a>CMFC 功能組合框::刪除所有專案

從清單框中刪除所有專案並清除編輯框。

```cpp
void RemoveAllItems();
```

### <a name="remarks"></a>備註

## <a name="cmfcribboncomboboxselectitem"></a><a name="selectitem"></a>CMFC 功能組合框::選擇項目

在清單框中選擇專案。

```cpp
BOOL SelectItem(int iIndex);
BOOL SelectItem(DWORD_PTR dwData);

BOOL SelectItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>參數

*iIndex*<br/>
[在]清單框中項的零基索引。

*dwData*<br/>
[在]與列表框中的項目關聯的數據。

*lpszText*<br/>
[在]清單框中項目的字串。

### <a name="return-value"></a>傳回值

如果方法成功,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

## <a name="cmfcribboncomboboxsetdropdownheight"></a><a name="setdropdownheight"></a>CMFC 功能組合Box::設定下拉高度

下下列表框時設置其高度。

```cpp
void SetDropDownHeight(int nHeight);
```

### <a name="parameters"></a>參數

*nHeight*<br/>
[在]清單框的高度(以像素為單位)。

### <a name="remarks"></a>備註

預設高度為 150 圖元。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonEdit 類別](../../mfc/reference/cmfcribbonedit-class.md)
