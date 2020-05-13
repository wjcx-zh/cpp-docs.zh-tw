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
ms.openlocfilehash: 5140d02c5acbbc430c3b4d175da1933c79c702b3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752350"
---
# <a name="cmfcheaderctrl-class"></a>CMFCHeaderCtrl Class

類`CMFCHeaderCtrl`支援對標頭控制件中的多列進行排序。

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
|[CMFCHeaderctrl::啟用多排序](#enablemultiplesort)|為當前標頭控制項啟用或禁用*多個欄位*模式。|
|[CMFCHeaderctrl::取得列格狀態](#getcolumnstate)|指示列是未排序,還是按升序或降序排序。|
|[CMFCHeaderctrl::獲取排序柱](#getsortcolumn)|檢索標頭控件中第一個排序列的零基索引。|
|`CMFCHeaderCtrl::GetThisClass`|框架用於獲取指向與此類類型關聯的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|
|[CMFCHeaderCtrl:正在提升](#isascending)|指示標題控制項中的任何列是否按升序排序。|
|[CMFCheaderctrl::IsDialog控制](#isdialogcontrol)|指示當前標頭控件的父視窗是否是對話方塊。|
|[CMFCHeaderctrl::是多排序](#ismultiplesort)|指示當前標頭控制件是否處於*多個列排序*模式。|
|[CMFCHeaderctrl::刪除排序列](#removesortcolumn)|從排序列清單中移除指定的欄位。|
|[CMFCHeaderctrl::SetSortColumn](#setsortcolumn)|設定標題控制項中指定列的排序順序。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMFCheaderctrl::在繪製專案](#ondrawitem)|由框架調用以繪製標題控制件列。|
|[CMFCheaderctrl::OndrawSortArrow](#ondrawsortarrow)|由框架調用以繪製排序箭頭。|
|[CMFCheaderctrl::在填充背景](#onfillbackground)|由框架調用以填充標頭控制列的背景。|

## <a name="example"></a>範例

下面的範例示範如何建構`CMFCHeaderCtrl`類的物件,以及如何為當前標頭控制項啟用*多個列排序*模式。

[!code-cpp[NVC_MFC_RibbonApp#24](../../mfc/reference/codesnippet/cpp/cmfcheaderctrl-class_1.cpp)]

## <a name="remarks"></a>備註

類`CMFCHeaderCtrl`在標題控制項列上繪製排序箭頭以指示該列已排序。 如果父清單控制件( [CMFCListCtrl 類](../../mfc/reference/cmfclistctrl-class.md)) 中的一組列可以同時排序,請使用*多個欄序*模式。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CHeaderCtrl](../../mfc/reference/cheaderctrl-class.md)

[CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md)

## <a name="requirements"></a>需求

**標題:** afxheaderctrl.h

## <a name="cmfcheaderctrlcmfcheaderctrl"></a><a name="cmfcheaderctrl"></a>CMFCHeaderCtrl::CMFCHeaderCtrl

建構 `CMFCHeaderCtrl` 物件。

```
CMFCHeaderCtrl::CMFCHeaderCtrl()
```

### <a name="remarks"></a>備註

此建構函數會將以下成員變數初始化到指定值:

|成員變數|值|
|---------------------|-----------|
|`m_bIsMousePressed`|FALSE|
|`m_bMultipleSort`|FALSE|
|`m_bAscending`|TRUE|
|`m_nHighlightedItem`|-1|
|`m_bTracked`|FALSE|
|`m_bIsDlgControl`|FALSE|
|`m_hFont`|NULL|

## <a name="cmfcheaderctrlenablemultiplesort"></a><a name="enablemultiplesort"></a>CMFCHeaderctrl::啟用多排序

為當前標頭控制項啟用或禁用*多個欄位*模式。

```cpp
void EnableMultipleSort(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>參數

*b 啟用*<br/>
[在]TRUE 啟用多列排序模式;FALSE 停用多個列排序模式,並從已排序列清單中刪除任何列。 預設值為 TRUE。

### <a name="remarks"></a>備註

使用此方法可啟用或禁用多個列排序模式。 如果標題控制項處於多個列排序模式,則兩個或多個列可以參與排序。

## <a name="cmfcheaderctrlgetcolumnstate"></a><a name="getcolumnstate"></a>CMFCHeaderctrl::取得列格狀態

指示列是未排序,還是按升序或降序排序。

```
int GetColumnState(int iColumn) const;
```

### <a name="parameters"></a>參數

*iColumn*<br/>
[在]列的零基索引。

### <a name="return-value"></a>傳回值

指示指定列的排序狀態的值。 下表列出可能的值：

|值|描述|
|-----------|-----------------|
|-1|按降序排序。|
|0|未排序。|
|1|按升序排序。|

### <a name="remarks"></a>備註

## <a name="cmfcheaderctrlgetsortcolumn"></a><a name="getsortcolumn"></a>CMFCHeaderctrl::獲取排序柱

檢索標頭控件中第一個排序列的零基索引。

```
int GetSortColumn() const;
```

### <a name="return-value"></a>傳回值

找不到已排序列的索引,或 -1。如果未找到已排序列。

### <a name="remarks"></a>備註

如果標頭控制器處於*多個列排序*模式,並且您在調試模式下編譯應用程式,則此方法斷言並建議您改用[CMFCHeaderCtrl::getColumnState](#getcolumnstate)方法。 如果標頭控制器處於多個列排序模式,並且您在零售模式下編譯應用程式,則此方法返回 -1。

## <a name="cmfcheaderctrlisascending"></a><a name="isascending"></a>CMFCHeaderCtrl:正在提升

指示標題控制項中的任何列是否按升序排序。

```
BOOL IsAscending() const;
```

### <a name="return-value"></a>傳回值

如果標題控制項中的任何列按升序排序,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

此方法返回的值用於在標頭控制項上顯示適當的排序箭頭。 使用[CMFCHeaderCtrl::SetSortColumn](#setsortcolumn)方法設置排序順序。

## <a name="cmfcheaderctrlisdialogcontrol"></a><a name="isdialogcontrol"></a>CMFCheaderctrl::IsDialog控制

指示當前標頭控件的父視窗是否是對話方塊。

```
BOOL IsDialogControl() const;
```

### <a name="return-value"></a>傳回值

如果當前標頭控件的父視窗是對話框,則為 TRUE;否則,FALSE。

## <a name="cmfcheaderctrlismultiplesort"></a><a name="ismultiplesort"></a>CMFCHeaderctrl::是多排序

指示當前標頭控制件是否處於*多個列排序*模式。

```
BOOL IsMultipleSort() const;
```

### <a name="return-value"></a>傳回值

如果啟用了多個列排序模式,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

使用[CMFCHeaderCtrl:啟用多排序](#enablemultiplesort)方法以啟用或禁用多個列排序模式。 如果標題控制項處於多個列排序模式,則兩個或多個列可以參與排序。

## <a name="cmfcheaderctrlondrawitem"></a><a name="ondrawitem"></a>CMFCheaderctrl::在繪製專案

由框架調用以繪製標題控制件列。

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
[在]指向設備上下文的指標。

*iItem*<br/>
[在]要繪製的項的零基索引。

*矩形*<br/>
[在]要繪製的項的邊界矩形。

*bIsPressed*<br/>
[在]TRUE 以按壓狀態繪製專案;否則,FALSE。

*bIs 突顯*<br/>
[在]TRUE 以突出顯示狀態繪製專案;如果為 TRUE,則為"TRUE",以"TRUE"狀態繪製專案。否則,FALSE。

## <a name="cmfcheaderctrlondrawsortarrow"></a><a name="ondrawsortarrow"></a>CMFCheaderctrl::OndrawSortArrow

由框架調用以繪製排序箭頭。

```
virtual void OnDrawSortArrow(
    CDC* pDC,
    CRect rectArrow);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向設備上下文的指標。

*雷克拉羅*<br/>
[在]排序箭頭的邊界矩形。

## <a name="cmfcheaderctrlonfillbackground"></a><a name="onfillbackground"></a>CMFCheaderctrl::在填充背景

由框架調用以填充標頭控制列的背景。

```
virtual void OnFillBackground(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向設備上下文的指標。

### <a name="remarks"></a>備註

## <a name="cmfcheaderctrlremovesortcolumn"></a><a name="removesortcolumn"></a>CMFCHeaderctrl::刪除排序列

從排序列清單中移除指定的欄位。

```cpp
void RemoveSortColumn(int iColumn);
```

### <a name="parameters"></a>參數

*iColumn*<br/>
[在]要刪除的列的零基索引。

## <a name="cmfcheaderctrlsetsortcolumn"></a><a name="setsortcolumn"></a>CMFCHeaderctrl::SetSortColumn

設定標題控制項中指定列的排序順序。

```cpp
void SetSortColumn(
    int iColumn,
    BOOL bAscending=TRUE,
    BOOL bAdd=FALSE);
```

### <a name="parameters"></a>參數

*iColumn*<br/>
[在]標頭控件列的零基索引。 如果此參數小於零,此方法將從排序列清單中刪除所有列。

*b 上升*<br/>
[在]指定*iColumn*參數指定的欄位順序順序。 真實設置提升順序;FALSE 以設置降序。 預設值為 TRUE。

*bAdd*<br/>
[在]TRUE 設定為*iColumn*參數指定的欄位的排序順序。

如果當前標頭控制器處於*多個欄序*模式,則此方法將指定的列添加到排序列清單中。 使用[CMFCHeaderCtrl:啟用多排序](#enablemultiplesort)以設置多個欄排序模式。

如果未設置多個列排序模式,並且此方法在調試模式下編譯,則此方法斷言。 如果未設置多個列排序模式,並且此方法在零售模式下編譯,則此方法首先從排序列清單中刪除所有列,然後將指定的列添加到清單中。

FALSE 首先從排序列清單中刪除所有列,然後將指定的列添加到清單中。 預設值為 FALSE。

### <a name="remarks"></a>備註

使用此方法設置列的排序順序。 如有必要,此方法將列添加到排序列清單中。 標題控制項使用排序順序繪製向上或向下點的排序箭頭。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCListCtrl 類別](../../mfc/reference/cmfclistctrl-class.md)
