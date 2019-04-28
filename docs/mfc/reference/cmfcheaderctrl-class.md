---
title: CMFCHeaderCtrl Class
ms.date: 11/04/2016
f1_keywords:
- CMFCHeaderCtrl
- AFXHEADERCTRL/CMFCHeaderCtrl
- AFXHEADERCTRL/CMFCHeaderCtrl::CMFCHeaderCtrl
- AFXHEADERCTRL/CMFCHeaderCtrl::EnableMultipleSort
- AFXHEADERCTRL/CMFCHeaderCtrl::GetColumnState
- AFXHEADERCTRL/CMFCHeaderCtrl::GetSortColumn
- AFXHEADERCTRL/CMFCHeaderCtrl::IsAscending
- AFXHEADERCTRL/CMFCHeaderCtrl::IsDialogControl
- AFXHEADERCTRL/CMFCHeaderCtrl::IsMultipleSort
- AFXHEADERCTRL/CMFCHeaderCtrl::RemoveSortColumn
- AFXHEADERCTRL/CMFCHeaderCtrl::SetSortColumn
- AFXHEADERCTRL/CMFCHeaderCtrl::OnDrawItem
- AFXHEADERCTRL/CMFCHeaderCtrl::OnDrawSortArrow
- AFXHEADERCTRL/CMFCHeaderCtrl::OnFillBackground
helpviewer_keywords:
- CMFCHeaderCtrl [MFC], CMFCHeaderCtrl
- CMFCHeaderCtrl [MFC], EnableMultipleSort
- CMFCHeaderCtrl [MFC], GetColumnState
- CMFCHeaderCtrl [MFC], GetSortColumn
- CMFCHeaderCtrl [MFC], IsAscending
- CMFCHeaderCtrl [MFC], IsDialogControl
- CMFCHeaderCtrl [MFC], IsMultipleSort
- CMFCHeaderCtrl [MFC], RemoveSortColumn
- CMFCHeaderCtrl [MFC], SetSortColumn
- CMFCHeaderCtrl [MFC], OnDrawItem
- CMFCHeaderCtrl [MFC], OnDrawSortArrow
- CMFCHeaderCtrl [MFC], OnFillBackground
ms.assetid: 2f5fbf7b-5c75-42db-9216-640b1628f777
ms.openlocfilehash: 86674e086da482e59b2711f5ba9154848ff05a6f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62218381"
---
# <a name="cmfcheaderctrl-class"></a>CMFCHeaderCtrl Class

`CMFCHeaderCtrl`類別支援排序標題控制項中的多個資料行。

## <a name="syntax"></a>語法

```
class CMFCHeaderCtrl : public CHeaderCtrl
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCHeaderCtrl::CMFCHeaderCtrl](#cmfcheaderctrl)|建構 `CMFCHeaderCtrl` 物件。|
|`CMFCHeaderCtrl::~CMFCHeaderCtrl`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort)|啟用或停用*多個資料行排序*目前標頭控制項模式。|
|[CMFCHeaderCtrl::GetColumnState](#getcolumnstate)|指出資料行並未排序，或以遞增或遞減順序排序。|
|[CMFCHeaderCtrl::GetSortColumn](#getsortcolumn)|擷取的第一個排序的資料行標題控制項中以零為起始的索引。|
|`CMFCHeaderCtrl::GetThisClass`|Framework 用來取得的指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|
|[CMFCHeaderCtrl::IsAscending](#isascending)|指出是否以遞增順序排序標題控制項中的任何資料行。|
|[CMFCHeaderCtrl::IsDialogControl](#isdialogcontrol)|指出對話方塊是否包含目前標頭控制項的父視窗。|
|[CMFCHeaderCtrl::IsMultipleSort](#ismultiplesort)|指出目前的標頭控制項處於*多個資料行排序*模式。|
|[CMFCHeaderCtrl::RemoveSortColumn](#removesortcolumn)|排序資料行清單中移除指定的資料行。|
|[CMFCHeaderCtrl::SetSortColumn](#setsortcolumn)|設定控制項中的指定資料行的排序次序。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMFCHeaderCtrl::OnDrawItem](#ondrawitem)|由架構呼叫以繪製標頭控制項資料行。|
|[CMFCHeaderCtrl::OnDrawSortArrow](#ondrawsortarrow)|由架構呼叫以繪製的排序箭號。|
|[CMFCHeaderCtrl::OnFillBackground](#onfillbackground)|由架構呼叫以填滿標頭控制項資料行的背景。|

## <a name="example"></a>範例

下列範例示範如何建構的物件`CMFCHeaderCtrl`類別，以及如何啟用*多個資料行排序*目前標頭控制項模式。

[!code-cpp[NVC_MFC_RibbonApp#24](../../mfc/reference/codesnippet/cpp/cmfcheaderctrl-class_1.cpp)]

## <a name="remarks"></a>備註

`CMFCHeaderCtrl`類別來表示已排序資料行的標頭控制項資料行上繪製的排序箭號。 使用*多個資料行排序*模式，如果一組父清單控制項中的資料行 ( [CMFCListCtrl 類別](../../mfc/reference/cmfclistctrl-class.md)) 可以在相同的時間排序。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CHeaderCtrl](../../mfc/reference/cheaderctrl-class.md)

[CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md)

## <a name="requirements"></a>需求

**標頭：** afxheaderctrl.h

##  <a name="cmfcheaderctrl"></a>  CMFCHeaderCtrl::CMFCHeaderCtrl

建構 `CMFCHeaderCtrl` 物件。

```
CMFCHeaderCtrl::CMFCHeaderCtrl()
```

### <a name="remarks"></a>備註

這個建構函式會初始化為指定值的下列成員變數：

|成員變數|值|
|---------------------|-----------|
|`m_bIsMousePressed`|false|
|`m_bMultipleSort`|false|
|`m_bAscending`|true|
|`m_nHighlightedItem`|-1|
|`m_bTracked`|false|
|`m_bIsDlgControl`|false|
|`m_hFont`|NULL|

##  <a name="enablemultiplesort"></a>  CMFCHeaderCtrl::EnableMultipleSort

啟用或停用*多個資料行排序*目前標頭控制項模式。

```
void EnableMultipleSort(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
[in]若要啟用多個資料行排序模式;，則為 TRUE若要停用多個資料行排序模式，並移除已排序的資料行清單中的任何資料行，則為 FALSE。 預設值為 TRUE。

### <a name="remarks"></a>備註

若要啟用或停用多個資料行排序模式中使用這個方法。 兩個或多個資料行可以參與排序標題控制項是否在多個資料行排序模式。

##  <a name="getcolumnstate"></a>  CMFCHeaderCtrl::GetColumnState

指出資料行是未排序，或以遞增或遞減順序排序。

```
int GetColumnState(int iColumn) const;
```

### <a name="parameters"></a>參數

*iColumn*<br/>
[in]資料行的以零為起始的索引。

### <a name="return-value"></a>傳回值

值，這個值表示指定的資料行的排序狀態。 下表列出可能的值：

|值|描述|
|-----------|-----------------|
|-1|以遞減順序排序。|
|0|未排序。|
|1|以遞增順序排序。|

### <a name="remarks"></a>備註

##  <a name="getsortcolumn"></a>  CMFCHeaderCtrl::GetSortColumn

擷取的第一個排序的資料行標題控制項中以零為起始的索引。

```
int GetSortColumn() const;
```

### <a name="return-value"></a>傳回值

排序的資料行或-1，如果不找到任何排序的資料行的索引。

### <a name="remarks"></a>備註

如果標頭控制項處於*多個資料行排序*模式，而且您編譯應用程式在偵錯模式中，這個方法會判斷提示，並提示您使用[CMFCHeaderCtrl::GetColumnState](#getcolumnstate)方法改為。 如果此標題控制項是在多個資料行排序模式編譯正式版本的模式中的應用程式，則這個方法會傳回-1。

##  <a name="isascending"></a>  CMFCHeaderCtrl::IsAscending

指出是否以遞增順序排序標題控制項中的任何資料行。

```
BOOL IsAscending() const;
```

### <a name="return-value"></a>傳回值

如果標題控制項中的任何資料行以遞增順序排序，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

這個方法傳回的值用來顯示標頭的控制項項目上的適當的排序箭號。 使用[CMFCHeaderCtrl::SetSortColumn](#setsortcolumn)方法來設定排序順序。

##  <a name="isdialogcontrol"></a>  CMFCHeaderCtrl::IsDialogControl

指出對話方塊是否包含目前標頭控制項的父視窗。

```
BOOL IsDialogControl() const;
```

### <a name="return-value"></a>傳回值

如果目前的標頭控制項的父視窗的對話方塊中，則為 TRUE否則為 FALSE。

##  <a name="ismultiplesort"></a>  CMFCHeaderCtrl::IsMultipleSort

指出目前的標頭控制項處於*多個資料行排序*模式。

```
BOOL IsMultipleSort() const;
```

### <a name="return-value"></a>傳回值

如果已啟用多個資料行排序模式，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

使用[CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort)方法可啟用或停用多個資料行排序模式。 兩個或多個資料行可以參與排序標題控制項是否在多個資料行排序模式。

##  <a name="ondrawitem"></a>  CMFCHeaderCtrl::OnDrawItem

由架構呼叫以繪製標頭控制項資料行。

```
virtual void OnDrawItem(
    CDC* pDC,
    int iItem,
    CRect rect,
    BOOL bIsPressed,
    BOOL bIsHighlighted);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[in]裝置內容指標。

*iItem*<br/>
[in]要繪製的項目以零為起始的索引。

*rect*<br/>
[in]要繪製之項目的週框。

*bIsPressed*<br/>
[in]TRUE 表示繪製項目處於已按下狀態;否則為 FALSE。

*bIsHighlighted*<br/>
[in]TRUE 表示繪製反白顯示的狀態; 中的項目否則為 FALSE。

##  <a name="ondrawsortarrow"></a>  CMFCHeaderCtrl::OnDrawSortArrow

由架構呼叫以繪製的排序箭號。

```
virtual void OnDrawSortArrow(
    CDC* pDC,
    CRect rectArrow);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[in]裝置內容指標。

*rectArrow*<br/>
[in]週框的排序箭號。

##  <a name="onfillbackground"></a>  CMFCHeaderCtrl::OnFillBackground

由架構呼叫以填滿標頭控制項資料行的背景。

```
virtual void OnFillBackground(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[in]裝置內容指標。

### <a name="remarks"></a>備註

##  <a name="removesortcolumn"></a>  CMFCHeaderCtrl::RemoveSortColumn

排序資料行清單中移除指定的資料行。

```
void RemoveSortColumn(int iColumn);
```

### <a name="parameters"></a>參數

*iColumn*<br/>
[in]要移除的資料行之以零起始的索引。

##  <a name="setsortcolumn"></a>  CMFCHeaderCtrl::SetSortColumn

設定控制項中的指定資料行的排序次序。

```
void SetSortColumn(
    int iColumn,
    BOOL bAscending=TRUE,
    BOOL bAdd=FALSE);
```

### <a name="parameters"></a>參數

*iColumn*<br/>
[in]標頭控制項資料行之以零起始的索引。 如果此參數小於零，則這個方法會移除所有資料行的排序資料行清單中。

*bAscending*<br/>
[in]指定資料行的排序次序所*iColumn*參數指定。 若要設定遞增順序，則為 TRUE若要設定遞減排序，則為 FALSE。 預設值為 TRUE。

*bAdd*<br/>
[in]True，以設定資料行的排序次序*iColumn*參數指定。

如果目前的標頭控制項處於*多個資料行排序*模式中，這個方法會將排序資料行清單中的指定資料行。 使用[CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort)來設定多個資料行排序模式。

如果未設定多個資料行排序模式，而且這個方法在偵錯模式中編譯，此方法會判斷提示。 如果未設定多個資料行排序模式，這個方法在零售模式中編譯，這個方法會先排序資料行 清單中移除所有資料行，然後將指定的資料行新增至清單。

為 FALSE，則第一個排序資料行清單中移除所有資料行，然後再加入至清單的 指定資料行。 預設值為 FALSE。

### <a name="remarks"></a>備註

這個方法可用於設定資料行的排序次序。 如有必要，這個方法會將資料行的排序資料行清單。 標題控制項使用的排序順序，來繪製點向上或向下的排序箭號。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCListCtrl 類別](../../mfc/reference/cmfclistctrl-class.md)
