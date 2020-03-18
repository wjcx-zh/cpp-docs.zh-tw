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
ms.openlocfilehash: 599a00af28ee5b8effbabbe5b334022ceb49f91a
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420313"
---
# <a name="cmfclistctrl-class"></a>CMFCListCtrl 類別

`CMFCListCtrl` 類別藉由支援[CMFCHeaderCtrl 類別](../../mfc/reference/cmfcheaderctrl-class.md)的 advanced 標頭控制項功能，擴充[CListCtrl 類別](../../mfc/reference/clistctrl-class.md)類別的功能。

## <a name="syntax"></a>語法

```
class CMFCListCtrl : public CListCtrl
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCListCtrl::EnableMarkSortedColumn](#enablemarksortedcolumn)|讓您能夠以不同的背景色彩來標示已排序的資料行。|
|[CMFCListCtrl::EnableMultipleSort](#enablemultiplesort)|啟用多重排序模式。|
|[CMFCListCtrl::GetHeaderCtrl](#getheaderctrl)|傳回加底線的標題控制項的參考。|
|[CMFCListCtrl::IsMultipleSort](#ismultiplesort)|檢查清單控制項是否處於多重排序模式。|
|[CMFCListCtrl::OnCompareItems](#oncompareitems)|當它必須比較兩個清單控制項專案時，由架構呼叫。|
|[CMFCListCtrl::OnGetCellBkColor](#ongetcellbkcolor)|當它必須決定個別資料格的背景色彩時，由架構呼叫。|
|[CMFCListCtrl::OnGetCellFont](#ongetcellfont)|當它必須取得所繪製儲存格的字型時，由架構呼叫。|
|[CMFCListCtrl::OnGetCellTextColor](#ongetcelltextcolor)|架構在必須決定個別資料格的文字色彩時呼叫。|
|[CMFCListCtrl::RemoveSortColumn](#removesortcolumn)|從已排序的資料行清單中移除排序資料行。|
|[CMFCListCtrl::SetSortColumn](#setsortcolumn)|設定目前排序的資料行和排序次序。|
|[CMFCListCtrl：： Sort](#sort)|排序清單控制項。|

## <a name="remarks"></a>備註

`CMFCListCtrl` 為[CListCtrl 類別](../../mfc/reference/clistctrl-class.md)類別提供兩種增強功能。 首先，它會透過在標頭上自動繪製排序箭號，指出資料行排序是可用的選項。 第二，它支援同時對多個資料行進行資料排序。

## <a name="example"></a>範例

下例示範如何在 `CMFCListCtrl` 類別中使用各種方法。 此範例顯示如何建立清單控制項、插入資料行、插入專案、設定專案的文字，以及設定清單控制項的字型。 此程式碼片段是[Visual Studio 示範範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_VisualStudioDemo#25](../../mfc/codesnippet/cpp/cmfclistctrl-class_1.h)]
[!code-cpp[NVC_MFC_VisualStudioDemo#26](../../mfc/codesnippet/cpp/cmfclistctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListCtrl](../../mfc/reference/clistctrl-class.md)

[CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)

## <a name="requirements"></a>需求

**標頭：** afxlistctrl。h

##  <a name="enablemarksortedcolumn"></a>CMFCListCtrl::EnableMarkSortedColumn

以不同的背景色彩標示已排序的資料行。

```
void EnableMarkSortedColumn(
    BOOL bMark = TRUE,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>參數

*bMark*<br/>
在布林值參數，決定是否要啟用不同的背景色彩。

*bRedraw*<br/>
在判斷是否要立即重繪控制項的布林值參數。

### <a name="remarks"></a>備註

`EnableMarkSortedColumn` 使用方法 `CDrawingManager::PixelAlpha` 來計算要用於排序資料行的色彩。 選取的色彩是依據一般背景色彩。

##  <a name="enablemultiplesort"></a>CMFCListCtrl::EnableMultipleSort

啟用排序清單控制項中資料列的多個資料行。

```
void EnableMultipleSort(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
在布林值，指定是否啟用多重資料行排序模式。

### <a name="remarks"></a>備註

當您根據多個資料行啟用排序時，資料行的確具有階層。 資料列會先依照主要資料行排序。 任何對等的值接著會根據優先順序，依據後續的每個資料行來排序。

##  <a name="getheaderctrl"></a>CMFCListCtrl::GetHeaderCtrl

傳回標頭控制項的參考。

```
virtual CMFCHeaderCtrl& GetHeaderCtrl();
```

### <a name="return-value"></a>傳回值

基礎[CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md)物件的參考。

### <a name="remarks"></a>備註

清單控制項的標題控制項是包含資料行標題的視窗。 它通常位於資料行的正上方。

##  <a name="ismultiplesort"></a>CMFCListCtrl::IsMultipleSort

檢查清單控制項目前是否支援對多個資料行進行排序。

```
BOOL IsMultipleSort() const;
```

### <a name="return-value"></a>傳回值

如果清單控制項支援多個排序，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

當[CMFCListCtrl 類別](../../mfc/reference/cmfclistctrl-class.md)支援多個排序時，使用者可以依照多個資料行來排序清單控制項中的資料。 若要啟用多個排序，請呼叫[CMFCListCtrl：： EnableMultipleSort](#enablemultiplesort)。

##  <a name="oncompareitems"></a>CMFCListCtrl::OnCompareItems

架構會在比較兩個專案時呼叫這個方法。

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>參數

*lParam1*<br/>
在要比較的第一個專案。

*lParam2*<br/>
在要比較的第二個專案。

*iColumn*<br/>
在這個方法所排序之資料行的索引。

### <a name="return-value"></a>傳回值

整數，表示兩個專案的相對位置。 負值表示第一個專案應該在第二個元素之前，正值表示第一個專案應該在第二個專案之後，而零表示兩個專案相等。

### <a name="remarks"></a>備註

預設的執行一律會傳回0。 覆寫此函式以提供您自己的排序演算法。

##  <a name="ongetcellbkcolor"></a>CMFCListCtrl::OnGetCellBkColor

當架構必須決定個別資料格的背景色彩時，會呼叫這個方法。

```
virtual COLORREF OnGetCellBkColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>參數

*nRow*<br/>
在有問題的資料格資料列。

*nColumn*<br/>
在有問題的資料格的資料行。

### <a name="return-value"></a>傳回值

COLORE光圈值，指定儲存格的背景色彩。

### <a name="remarks"></a>備註

`OnGetCellBkColor` 的預設執行不會使用提供的輸入參數，而是只會呼叫 `GetBkColor`。 因此，整個清單控制項預設會有相同的背景色彩。 您可以覆寫衍生類別中的 `OnGetCellBkColor`，以不同的背景色彩標記個別的儲存格。

##  <a name="ongetcellfont"></a>CMFCListCtrl::OnGetCellFont

當此架構取得個別資料格的字型時，會呼叫這個方法。

```
virtual HFONT OnGetCellFont(
    int nRow,
    int nColumn,
    DWORD dwData = 0);
```

### <a name="parameters"></a>參數

*nRow*<br/>
在有問題的資料格資料列。

*nColumn*<br/>
在有問題的資料格的資料行。

*dwData*<br/>
在使用者定義的資料。 預設的執行不會使用此參數。

### <a name="return-value"></a>傳回值

用於目前儲存格之字型的控制碼。

### <a name="remarks"></a>備註

根據預設，這個方法會傳回 Null。 清單控制項中的所有儲存格都具有相同的字型。 覆寫這個方法，為不同的儲存格提供不同的字型。

##  <a name="ongetcelltextcolor"></a>CMFCListCtrl::OnGetCellTextColor

當架構必須決定個別資料格的文字色彩時，會呼叫這個方法。

```
virtual COLORREF OnGetCellTextColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>參數

*nRow*<br/>
在有問題的資料格資料列。

*nColumn*<br/>
在有問題的資料格的資料行。

### <a name="return-value"></a>傳回值

COLORE光圈值，指定儲存格的文字色彩。

### <a name="remarks"></a>備註

根據預設，不論輸入參數為何，這個方法都會呼叫 `GetTextColor`。 整個清單控制項將會有相同的文字色彩。 您可以覆寫衍生類別中的 `OnGetCellTextColor`，將個別的資料格標記為不同的文字色彩。

##  <a name="removesortcolumn"></a>CMFCListCtrl::RemoveSortColumn

從已排序的資料行清單中移除排序資料行。

```
void RemoveSortColumn(int iColumn);
```

### <a name="parameters"></a>參數

*iColumn*<br/>
在要移除的資料行。

### <a name="remarks"></a>備註

這個方法會從標題控制項中移除排序資料行。 它會呼叫[CMFCHeaderCtrl：： RemoveSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#removesortcolumn)。

##  <a name="setsortcolumn"></a>CMFCListCtrl::SetSortColumn

設定目前排序的資料行和排序次序。

```
void SetSortColumn(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>參數

*iColumn*<br/>
在要排序的資料行。

*bAscending*<br/>
在指定排序次序的布林值。

*bAdd*<br/>
在布林值，指定方法是否將*iColumn*所指定的資料行加入至排序資料行清單。

### <a name="remarks"></a>備註

這個方法會使用[CMFCHeaderCtrl：： SetSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#setsortcolumn)方法，將輸入參數傳遞至標頭控制項。

##  <a name="sort"></a>CMFCListCtrl：： Sort

排序清單控制項。

```
virtual void Sort(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>參數

*iColumn*<br/>
在要排序的資料行。

*bAscending*<br/>
在指定排序次序的布林值。

*bAdd*<br/>
在布林值，指定這個方法是否將*iColumn*所指定的資料行加入至排序資料行清單。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CListCtrl 類別](../../mfc/reference/clistctrl-class.md)
