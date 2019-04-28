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
ms.openlocfilehash: 89007ea3eb7fd0aef28caadf439195b4090a05d8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62237318"
---
# <a name="cmfcribboncombobox-class"></a>CMFCRibbonComboBox 類別

`CMFCRibbonComboBox`類別會實作可以加入功能區列、 功能區面板或功能區快顯功能表的下拉式方塊控制項。

## <a name="syntax"></a>語法

```
class CMFCRibbonComboBox : public CMFCRibbonEdit
```

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCRibbonComboBox::CMFCRibbonComboBox](#cmfcribboncombobox)|建構 CMFCRibbonComboBox 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCRibbonComboBox::AddItem](#additem)|將唯一的項目附加至清單方塊中。|
|[CMFCRibbonComboBox::DeleteItem](#deleteitem)|從清單方塊中，刪除指定的項目。|
|[CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)|指定當它下拉，清單方塊是否可以變更大小。|
|[CMFCRibbonComboBox::FindItem](#finditem)|傳回符合指定的字串清單方塊中的第一個項目的索引。|
|[CMFCRibbonComboBox::GetCount](#getcount)|在清單方塊中，傳回的項目數。|
|[CMFCRibbonComboBox::GetCurSel](#getcursel)|在清單方塊中，取得目前選取項目的索引。|
|[CMFCRibbonComboBox::GetDropDownHeight](#getdropdownheight)|當清單方塊已下拉，請取得清單方塊的高度。|
|[CMFCRibbonComboBox::GetIntermediateSize](#getintermediatesize)|傳回的大小下拉式方塊的中繼模式中所示。|
|[CMFCRibbonComboBox::GetItem](#getitem)|傳回字串與清單方塊中的指定索引處的項目相關聯。|
|[CMFCRibbonComboBox::GetItemData](#getitemdata)|傳回與清單方塊中的指定索引處的項目相關聯的資料。|
|[CMFCRibbonComboBox::HasEditBox](#haseditbox)|指出控制項是否包含編輯方塊。|
|[CMFCRibbonComboBox::IsResizeDropDownList](#isresizedropdownlist)|指出可以調整大小的清單方塊。|
|[CMFCRibbonComboBox::OnSelectItem](#onselectitem)|當使用者選取項目在清單方塊中，由架構呼叫。|
|[CMFCRibbonComboBox::RemoveAllItems](#removeallitems)|從清單方塊會刪除所有項目，並清除 [編輯] 方塊。|
|[CMFCRibbonComboBox::SelectItem](#selectitem)|在清單方塊中選取項目。|
|[CMFCRibbonComboBox::SetDropDownHeight](#setdropdownheight)|向下拖曳時，請設定清單方塊的高度。|

## <a name="remarks"></a>備註

功能區下拉式方塊是由清單方塊，結合靜態標籤或使用者可以編輯的標籤所組成。 您必須指定當您建立您的功能區下拉式方塊，您需要哪種的類型。

## <a name="example"></a>範例

下列範例示範如何建構的物件`CMFCRibbonComboBox`類別、 新增項目至下拉式方塊、 下拉式方塊中，選取項目和面板加入下拉式方塊。

[!code-cpp[NVC_MFC_RibbonApp#11](../../mfc/reference/codesnippet/cpp/cmfcribboncombobox-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)

[CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)

## <a name="requirements"></a>需求

**標頭：** afxribboncombobox.h

##  <a name="additem"></a>  CMFCRibbonComboBox::AddItem

將唯一的項目附加至清單方塊中。

```
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>參數

*lpszItem*<br/>
[in]要加入之項目的字串。

*dwData*<br/>
[in]要加入的項目相關聯的資料。

### <a name="return-value"></a>傳回值

附加的項目以零為起始的索引。

##  <a name="cmfcribboncombobox"></a>  CMFCRibbonComboBox::CMFCRibbonComboBox

建構 `CMFCRibbonComboBox` 物件。

```
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
[in]下拉式方塊的識別碼。

*bHasEditBox*<br/>
[in]如果您想要編輯方塊內的控制項，則為 TRUEFALSE 否則。

*nWidth*<br/>
[in]像素為單位; 中的下拉式方塊的寬度-1 則代表的預設寬度。

*lpszLabel*<br/>
[in]下拉式方塊的顯示標籤。

*nImage*<br/>
[in]下拉式方塊的小型影像索引。

### <a name="remarks"></a>備註

預設寬度是 108 像素為單位。

##  <a name="deleteitem"></a>  CMFCRibbonComboBox::DeleteItem

從清單方塊中，刪除指定的項目。

```
BOOL DeleteItem(int iIndex);
BOOL DeleteItem(DWORD_PTR dwData);

BOOL DeleteItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>參數

*iIndex*<br/>
[in]要刪除之項目的以零為起始的索引。

*dwData*<br/>
[in]要刪除的項目相關聯的資料。

*lpszText*<br/>
[in]要刪除之項目的字串。 如果有多個相同的字串項目，則會刪除第一個項目。

### <a name="return-value"></a>傳回值

如果已刪除指定的項目，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="enabledropdownlistresize"></a>  CMFCRibbonComboBox::EnableDropDownListResize

指定當它下拉，清單方塊是否可以變更大小。

```
void EnableDropDownListResize(BOOL bEnable=FALSE);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
[in] True 表示啟用調整大小;若要停用調整大小，則為 FALSE。

### <a name="remarks"></a>備註

啟用調整大小後，清單方塊會變更大小，以符合它所顯示的項目。

##  <a name="finditem"></a>  CMFCRibbonComboBox::FindItem

傳回符合指定的字串清單方塊中的第一個項目的索引。

```
int FindItem(LPCTSTR lpszText) const;
```

### <a name="parameters"></a>參數

*lpszText*<br/>
[in]在清單方塊項目的字串。

### <a name="return-value"></a>傳回值

項目的以零起始的索引或-1，如果找不到項目。

### <a name="remarks"></a>備註

##  <a name="getcount"></a>  CMFCRibbonComboBox::GetCount

在清單方塊中，傳回的項目數。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>傳回值

在清單方塊中或 0，如果清單方塊中不包含任何項目中的項目數目。

### <a name="remarks"></a>備註

##  <a name="getcursel"></a>  CMFCRibbonComboBox::GetCurSel

在清單方塊中，取得目前選取項目的索引。

```
int GetCurSel() const;
```

### <a name="return-value"></a>傳回值

清單方塊中目前選取項目的以零起始的索引則為-1 會選取任何項目。

##  <a name="getdropdownheight"></a>  CMFCRibbonComboBox::GetDropDownHeight

當清單方塊已下拉，請取得清單方塊的高度。

```
int GetDropDownHeight();
```

### <a name="return-value"></a>傳回值

像素為單位，清單方塊的高度。

### <a name="remarks"></a>備註

##  <a name="getintermediatesize"></a>  CMFCRibbonComboBox::GetIntermediateSize

傳回的大小下拉式方塊的中繼模式中所示。

```
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[in]下拉式方塊的裝置內容指標。

### <a name="return-value"></a>傳回值

下拉式方塊的大小。

### <a name="remarks"></a>備註

顯示小型影像時，傳回的大小根據下拉式方塊的大小。

##  <a name="getitem"></a>  CMFCRibbonComboBox::GetItem

傳回字串與清單方塊中的指定索引處的項目相關聯。

```
LPCTSTR GetItem(int iIndex) const;
```

### <a name="parameters"></a>參數

*iIndex*<br/>
[in]清單方塊中的項目以零為起始的索引。

### <a name="return-value"></a>傳回值

項目; 相關聯的字串指標否則為 NULL 的索引參數無效，則索引參數是-1 且沒有在下拉式方塊中選取的項目。

### <a name="remarks"></a>備註

##  <a name="getitemdata"></a>  CMFCRibbonComboBox::GetItemData

傳回與清單方塊中的指定索引處的項目相關聯的資料。

```
DWORD_PTR GetItemData(int iIndex) const;
```

### <a name="parameters"></a>參數

*iIndex*<br/>
[in]清單方塊中的項目以零為起始的索引。

### <a name="return-value"></a>傳回值

與項目; 相關聯的資料則為 0 的項目不存在，則索引參數是-1，而且在清單方塊中沒有選取項目。

##  <a name="haseditbox"></a>  CMFCRibbonComboBox::HasEditBox

指出控制項是否包含編輯方塊。

```
BOOL HasEditBox() const;
```

### <a name="return-value"></a>傳回值

如果控制項包含編輯方塊中，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="isresizedropdownlist"></a>  CMFCRibbonComboBox::IsResizeDropDownList

指出可以調整大小的清單方塊。

```
BOOL IsResizeDropDownList() const;
```

### <a name="return-value"></a>傳回值

如果可以調整清單方塊的大小;，則為 TRUE。否則為 FALSE。 [CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)

### <a name="remarks"></a>備註

您可以使用調整大小的清單方塊來啟用[CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)方法。

##  <a name="onselectitem"></a>  CMFCRibbonComboBox::OnSelectItem

當使用者選取項目在清單方塊中，由架構呼叫。

```
virtual void OnSelectItem(int nItem);
```

### <a name="parameters"></a>參數

*nItem*<br/>
[in]選取的項目索引。

### <a name="remarks"></a>備註

如果您想要處理使用者輸入選取範圍，請覆寫這個方法。

##  <a name="removeallitems"></a>  CMFCRibbonComboBox::RemoveAllItems

從清單方塊會刪除所有項目，並清除 [編輯] 方塊。

```
void RemoveAllItems();
```

### <a name="remarks"></a>備註

##  <a name="selectitem"></a>  CMFCRibbonComboBox::SelectItem

在清單方塊中選取項目。

```
BOOL SelectItem(int iIndex);
BOOL SelectItem(DWORD_PTR dwData);

BOOL SelectItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>參數

*iIndex*<br/>
[in]清單方塊中的項目以零為起始的索引。

*dwData*<br/>
[in]使用清單方塊中的項目相關聯的資料。

*lpszText*<br/>
[in]在清單方塊項目的字串。

### <a name="return-value"></a>傳回值

如果方法成功，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="setdropdownheight"></a>  CMFCRibbonComboBox::SetDropDownHeight

向下拖曳時，請設定清單方塊的高度。

```
void SetDropDownHeight(int nHeight);
```

### <a name="parameters"></a>參數

*nHeight*<br/>
[in]像素為單位，清單方塊的高度。

### <a name="remarks"></a>備註

預設高度為 150 個像素。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonEdit 類別](../../mfc/reference/cmfcribbonedit-class.md)
