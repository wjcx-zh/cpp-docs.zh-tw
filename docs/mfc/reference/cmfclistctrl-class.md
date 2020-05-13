---
title: CMFCListCtrl 類別
ms.date: 07/30/2019
f1_keywords:
- CMFCListCtrl
- AFXLISTCTRL/CMFCListCtrl
- AFXLISTCTRL/CMFCListCtrl::EnableMarkSortedColumn
- AFXLISTCTRL/CMFCListCtrl::EnableMultipleSort
- AFXLISTCTRL/CMFCListCtrl::GetHeaderCtrl
- AFXLISTCTRL/CMFCListCtrl::IsMultipleSort
- AFXLISTCTRL/CMFCListCtrl::OnCompareItems
- AFXLISTCTRL/CMFCListCtrl::OnGetCellBkColor
- AFXLISTCTRL/CMFCListCtrl::OnGetCellFont
- AFXLISTCTRL/CMFCListCtrl::OnGetCellTextColor
- AFXLISTCTRL/CMFCListCtrl::RemoveSortColumn
- AFXLISTCTRL/CMFCListCtrl::SetSortColumn
- AFXLISTCTRL/CMFCListCtrl::Sort
helpviewer_keywords:
- CMFCListCtrl [MFC], EnableMarkSortedColumn
- CMFCListCtrl [MFC], EnableMultipleSort
- CMFCListCtrl [MFC], GetHeaderCtrl
- CMFCListCtrl [MFC], IsMultipleSort
- CMFCListCtrl [MFC], OnCompareItems
- CMFCListCtrl [MFC], OnGetCellBkColor
- CMFCListCtrl [MFC], OnGetCellFont
- CMFCListCtrl [MFC], OnGetCellTextColor
- CMFCListCtrl [MFC], RemoveSortColumn
- CMFCListCtrl [MFC], SetSortColumn
- CMFCListCtrl [MFC], Sort
ms.assetid: 50d16aee-138c-4f34-8690-cb75d544ef2e
ms.openlocfilehash: 099ec086bd95a1180af4cf5a8f6a9fa7f1d099ea
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754239"
---
# <a name="cmfclistctrl-class"></a>CMFCListCtrl 類別

該`CMFCListCtrl`類通過支援[CMFCHeaderCtrl 類](../../mfc/reference/cmfcheaderctrl-class.md)的高級標頭控制功能擴展[了 CListCtrl 類](../../mfc/reference/clistctrl-class.md)的功能。

## <a name="syntax"></a>語法

```
class CMFCListCtrl : public CListCtrl
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCListctrl::啟用標籤排序](#enablemarksortedcolumn)|能夠用不同的背景顏色標記已排序的列。|
|[CMFCListctrl::啟用多排序](#enablemultiplesort)|啟用多個排序模式。|
|[CMFCListCtrl::獲取頭Ctrl](#getheaderctrl)|返回對帶下劃線標頭控件的引用。|
|[CMFCListctrl::是多排序](#ismultiplesort)|檢查清單控制項是否處於多個排序模式。|
|[CMFCListctrl::上比較專案](#oncompareitems)|當框架必須比較兩個清單控制項時,由框架調用。|
|[CMFCListctrl::在GetCellBkColor上](#ongetcellbkcolor)|當框架必須確定單個單元格的背景顏色時,由框架調用。|
|[CMFCListctrl::在Getcellcellfont](#ongetcellfont)|當框架必須獲取所繪製的單元格的字體時,由框架調用。|
|[CMFCListctrl::在獲取細胞文字顏色](#ongetcelltextcolor)|當框架必須確定單個儲存格的文本顏色時,由框架調用。|
|[CMFCListctrl::刪除排序列](#removesortcolumn)|從排序列清單中移除排序。|
|[CMFCListctrl::SetSortColumn](#setsortcolumn)|設置當前排序列和排序順序。|
|[CMFCListctrl:排序](#sort)|對清單控制件進行排序。|

## <a name="remarks"></a>備註

`CMFCListCtrl`提供了[CListCtrl 類](../../mfc/reference/clistctrl-class.md)的兩個增強功能。 首先,它指示列排序是一個可用選項,通過在標題上自動繪製排序箭頭。 其次,它支持同時對多個列的數據排序。

## <a name="example"></a>範例

下例示範如何在 `CMFCListCtrl` 類別中使用各種方法。 該範例展示如何建立清單控制項、插入列、插入項、設定項的文本以及設置清單控制件的字型。 此代碼段是[可視化工作室演示範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_VisualStudioDemo#25](../../mfc/codesnippet/cpp/cmfclistctrl-class_1.h)]
[!code-cpp[NVC_MFC_VisualStudioDemo#26](../../mfc/codesnippet/cpp/cmfclistctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListCtrl](../../mfc/reference/clistctrl-class.md)

[CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)

## <a name="requirements"></a>需求

**標題:** afxlistctrl.h

## <a name="cmfclistctrlenablemarksortedcolumn"></a><a name="enablemarksortedcolumn"></a>CMFCListctrl::啟用標籤排序

用不同的背景顏色標記已排序的欄。

```cpp
void EnableMarkSortedColumn(
    BOOL bMark = TRUE,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>參數

*b馬克*<br/>
[在]確定是否啟用其他背景顏色的布林參數。

*bredraw*<br/>
[在]確定是否立即重繪控件的布爾參數。

### <a name="remarks"></a>備註

`EnableMarkSortedColumn`使用方法`CDrawingManager::PixelAlpha`計算對已排序列使用的顏色。 拾取的顏色基於常規背景顏色。

## <a name="cmfclistctrlenablemultiplesort"></a><a name="enablemultiplesort"></a>CMFCListctrl::啟用多排序

開啟按多個欄位中的資料列進行排序。

```cpp
void EnableMultipleSort(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>參數

*b 啟用*<br/>
[在]指定是否啟用多個欄位模式的布林。

### <a name="remarks"></a>備註

當您基於多個列啟用排序時,列確實具有層次結構。 數據行將首先按主列排序。 然後,根據優先順序按每個後續列對任何等效值進行排序。

## <a name="cmfclistctrlgetheaderctrl"></a><a name="getheaderctrl"></a>CMFCListCtrl::獲取頭Ctrl

返回對標頭控件的引用。

```
virtual CMFCHeaderCtrl& GetHeaderCtrl();
```

### <a name="return-value"></a>傳回值

對基礎[CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md)物件的引用。

### <a name="remarks"></a>備註

清單控制項標頭控制檔是包含欄標題的視窗。 它通常位於列正上方。

## <a name="cmfclistctrlismultiplesort"></a><a name="ismultiplesort"></a>CMFCListctrl::是多排序

檢查清單控制項目前是否支援對多個欄列進行排序。

```
BOOL IsMultipleSort() const;
```

### <a name="return-value"></a>傳回值

如果清單控制件支援多個排序,則為 TRUE;如果清單控制件支援多個排序。"否則。

### <a name="remarks"></a>備註

當[CMFCListCtrl 類](../../mfc/reference/cmfclistctrl-class.md)支援多個排序時,用戶可以按多個列對清單控制項中的數據進行排序。 要啟用多個排序,請致電[CMFCListCtrl::開啟多排序](#enablemultiplesort)。

## <a name="cmfclistctrloncompareitems"></a><a name="oncompareitems"></a>CMFCListctrl::上比較專案

框架在比較兩個專案時調用此方法。

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>參數

*lParam1*<br/>
[在]要比較的第一項。

*lParam2*<br/>
[在]要比較的第二個專案。

*iColumn*<br/>
[在]此方法正在排序的列的索引。

### <a name="return-value"></a>傳回值

指示兩個項的相對位置的整數。 負值表示第一個項應位於第二個項之前,正值表示第一個項應遵循第二個項,零表示兩個項等效。

### <a name="remarks"></a>備註

默認實現始終返回 0。 重寫此函數以提供您自己的排序演演算法。

## <a name="cmfclistctrlongetcellbkcolor"></a><a name="ongetcellbkcolor"></a>CMFCListctrl::在GetCellBkColor上

當框架必須確定單個儲存格的背景顏色時,該框架將調用此方法。

```
virtual COLORREF OnGetCellBkColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>參數

*nRow*<br/>
[在]有問題的單元格的行。

*nColumn*<br/>
[在]有問題的單元格的列。

### <a name="return-value"></a>傳回值

指定儲存格背景顏色的 COLOREF 值。

### <a name="remarks"></a>備註

預設`OnGetCellBkColor`可使用提供的輸入參數,而只是呼叫`GetBkColor`。 因此,默認情況下,整個清單控制項將具有相同的背景顏色。 可以在派生類`OnGetCellBkColor`中重寫以標記具有單獨背景顏色的各個單元格。

## <a name="cmfclistctrlongetcellfont"></a><a name="ongetcellfont"></a>CMFCListctrl::在Getcellcellfont

當框架獲取單個單元格的字體時,它將調用此方法。

```
virtual HFONT OnGetCellFont(
    int nRow,
    int nColumn,
    DWORD dwData = 0);
```

### <a name="parameters"></a>參數

*nRow*<br/>
[在]有問題的單元格的行。

*nColumn*<br/>
[在]有問題的單元格的列。

*dwData*<br/>
[在]使用者定義的數據。 預設實現不使用此參數。

### <a name="return-value"></a>傳回值

用於當前儲存格的字型的句柄。

### <a name="remarks"></a>備註

預設情況下,此方法傳回 NULL。 清單控制項的所有儲存格具有相同的字型。 重寫此方法,為不同的單元格提供不同的字體。

## <a name="cmfclistctrlongetcelltextcolor"></a><a name="ongetcelltextcolor"></a>CMFCListctrl::在獲取細胞文字顏色

當框架必須確定單個儲存格的文本顏色時,它將調用此方法。

```
virtual COLORREF OnGetCellTextColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>參數

*nRow*<br/>
[在]有問題的單元格的行。

*nColumn*<br/>
[在]有問題的單元格的列。

### <a name="return-value"></a>傳回值

指定儲存格的文字顏色的 COLOREF 值。

### <a name="remarks"></a>備註

默認情況下,此方法調用`GetTextColor`,而不考慮輸入參數。 整個清單控制項將具有相同的文字顏色。 可以在派生類`OnGetCellTextColor`中重寫以標記具有單獨文本顏色的各個單元格。

## <a name="cmfclistctrlremovesortcolumn"></a><a name="removesortcolumn"></a>CMFCListctrl::刪除排序列

從排序列清單中移除排序。

```cpp
void RemoveSortColumn(int iColumn);
```

### <a name="parameters"></a>參數

*iColumn*<br/>
[在]要刪除的欄。

### <a name="remarks"></a>備註

此方法從標頭控制項中刪除排序列。 它呼叫[CMFCHeaderCtrl::刪除排序](../../mfc/reference/cmfcheaderctrl-class.md#removesortcolumn)。

## <a name="cmfclistctrlsetsortcolumn"></a><a name="setsortcolumn"></a>CMFCListctrl::SetSortColumn

設置當前排序列和排序順序。

```cpp
void SetSortColumn(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>參數

*iColumn*<br/>
[在]要排序的列。

*b 上升*<br/>
[在]指定排序順序的布林。

*bAdd*<br/>
[在]指定方法是否將*iColumn*指示的列添加到排序列清單中的布林。

### <a name="remarks"></a>備註

此方法使用[CMFCHeaderCtrl::setSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#setsortcolumn)的方法將輸入參數傳遞給標頭控制項。

## <a name="cmfclistctrlsort"></a><a name="sort"></a>CMFCListctrl:排序

對清單控制件進行排序。

```
virtual void Sort(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>參數

*iColumn*<br/>
[在]要排序的列。

*b 上升*<br/>
[在]指定排序順序的布林。

*bAdd*<br/>
[在]指定此方法是否將*iColumn*指示的列添加到排序列清單中的布林。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CListCtrl 類別](../../mfc/reference/clistctrl-class.md)
