---
title: CMFCHeaderCtrl 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6af0859811ad4064c12f6e4ef8d470437fe3ded9
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37037657"
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
|[CMFCHeaderCtrl::GetColumnState](#getcolumnstate)|指出資料行未排序，或以遞增或遞減順序排序。|  
|[CMFCHeaderCtrl::GetSortColumn](#getsortcolumn)|擷取的第一個標題控制項中排序資料行以零為起始的索引。|  
|`CMFCHeaderCtrl::GetThisClass`|由架構用來取得指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|  
|[CMFCHeaderCtrl::IsAscending](#isascending)|指出是否以遞增順序排序標題控制項中的任何資料行。|  
|[CMFCHeaderCtrl::IsDialogControl](#isdialogcontrol)|指出對話方塊是否包含目前標頭控制項的父視窗。|  
|[CMFCHeaderCtrl::IsMultipleSort](#ismultiplesort)|指出是否在目前的標頭控制項*多個資料行排序*模式。|  
|[CMFCHeaderCtrl::RemoveSortColumn](#removesortcolumn)|排序資料行清單中移除指定的資料行。|  
|[CMFCHeaderCtrl::SetSortColumn](#setsortcolumn)|設定控制項中的指定資料行的排序次序。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCHeaderCtrl::OnDrawItem](#ondrawitem)|由架構呼叫以繪製的標頭控制項的資料行。|  
|[CMFCHeaderCtrl::OnDrawSortArrow](#ondrawsortarrow)|由架構呼叫以繪製排序箭號。|  
|[CMFCHeaderCtrl::OnFillBackground](#onfillbackground)|標頭控制資料行的背景填滿架構呼叫。|  
  
## <a name="example"></a>範例  
 下列範例示範如何建構的物件`CMFCHeaderCtrl`類別，以及如何啟用*多個資料行排序*目前標頭控制項模式。  
  
 [!code-cpp[NVC_MFC_RibbonApp#24](../../mfc/reference/codesnippet/cpp/cmfcheaderctrl-class_1.cpp)]  
  
## <a name="remarks"></a>備註  
 `CMFCHeaderCtrl`類別繪製排序箭號，表示已排序的資料行的標頭控制項的資料行上。 使用*多個資料行排序*如果一組父系清單控制項中的資料行模式 ( [CMFCListCtrl 類別](../../mfc/reference/cmfclistctrl-class.md)) 可以在同一時間排序。  
  
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
 這個建構函式會初始化為指定的值的下列成員變數：  
  
|成員變數|值|  
|---------------------|-----------|  
|`m_bIsMousePressed`|`FALSE`|  
|`m_bMultipleSort`|`FALSE`|  
|`m_bAscending`|`TRUE`|  
|`m_nHighlightedItem`|-1|  
|`m_bTracked`|`FALSE`|  
|`m_bIsDlgControl`|`FALSE`|  
|`m_hFont`|`NULL`|  
  
##  <a name="enablemultiplesort"></a>  CMFCHeaderCtrl::EnableMultipleSort  
 啟用或停用*多個資料行排序*目前標頭控制項模式。  
  
```  
void EnableMultipleSort(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in]*bEnable*  
 `TRUE` 若要啟用多個資料行排序模式;`FALSE`停用多個資料行排序模式，以及從已排序的資料行的清單中移除任何資料行。 預設值是 `TRUE`。  
  
### <a name="remarks"></a>備註  
 若要啟用或停用多個資料行排序模式中使用這個方法。 兩個或多個資料行可以參與排序標題控制項是否在多個資料行排序模式。  
  
##  <a name="getcolumnstate"></a>  CMFCHeaderCtrl::GetColumnState  
 指出資料行是未排序，或以遞增或遞減順序排序。  
  
```  
int GetColumnState(int iColumn) const;  
```  
  
### <a name="parameters"></a>參數  
 [in]*iColumn*  
 在資料行以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 值，表示指定的資料行的排序狀態。 下表列出可能的值：  
  
|值|描述|  
|-----------|-----------------|  
|-1|以遞減順序排序。|  
|0|未排序。|  
|1|以遞增順序排序。|  
  
### <a name="remarks"></a>備註  
  
##  <a name="getsortcolumn"></a>  CMFCHeaderCtrl::GetSortColumn  
 擷取的第一個標題控制項中排序資料行以零為起始的索引。  
  
```  
int GetSortColumn() const;  
```  
  
### <a name="return-value"></a>傳回值  
 排序的資料行，則為-1 位於任何已排序的資料行的索引。  
  
### <a name="remarks"></a>備註  
 如果此標題控制項處於*多個資料行排序*模式，而且您編譯應用程式在偵錯模式中，這個方法會判斷提示，提示您使用[CMFCHeaderCtrl::GetColumnState](#getcolumnstate)方法改為。 如果此標題控制項在多個資料行排序模式，且編譯正式版本的模式中的應用程式，這個方法會傳回-1。  
  
##  <a name="isascending"></a>  CMFCHeaderCtrl::IsAscending  
 指出是否以遞增順序排序標題控制項中的任何資料行。  
  
```  
BOOL IsAscending() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果標題控制項中的任何資料行以遞增順序排序否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法傳回的值用於標頭控制項項目中顯示適當的排序箭號。 使用[CMFCHeaderCtrl::SetSortColumn](#setsortcolumn)設定排序順序的方法。  
  
##  <a name="isdialogcontrol"></a>  CMFCHeaderCtrl::IsDialogControl  
 指出對話方塊是否包含目前標頭控制項的父視窗。  
  
```  
BOOL IsDialogControl() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果目前的標頭控制項的父視窗對話方塊。否則， `FALSE`。  
  
##  <a name="ismultiplesort"></a>  CMFCHeaderCtrl::IsMultipleSort  
 指出是否在目前的標頭控制項*多個資料行排序*模式。  
  
```  
BOOL IsMultipleSort() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果已啟用多個資料行排序模式;否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 使用[CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort)方法啟用或停用多個資料行排序模式。 兩個或多個資料行可以參與排序標題控制項是否在多個資料行排序模式。  
  
##  <a name="ondrawitem"></a>  CMFCHeaderCtrl::OnDrawItem  
 由架構呼叫以繪製的標頭控制項的資料行。  
  
```  
virtual void OnDrawItem(
    CDC* pDC,  
    int iItem,  
    CRect rect,  
    BOOL bIsPressed,  
    BOOL bIsHighlighted);
```  
  
### <a name="parameters"></a>參數  
 [in]*pDC*  
 裝置內容的指標。  
  
 [in]*iItem*  
 要繪製的項目以零為起始的索引。  
  
 [in]*rect*  
 要繪製之項目的週框。  
  
 [in]*bIsPressed*  
 `TRUE` 若要在按下狀態; 繪製項目否則， `FALSE`。  
  
 [in]*bIsHighlighted*  
 `TRUE` 若要繪製項目中反白顯示的狀態。否則， `FALSE`。  
  
##  <a name="ondrawsortarrow"></a>  CMFCHeaderCtrl::OnDrawSortArrow  
 由架構呼叫以繪製排序箭號。  
  
```  
virtual void OnDrawSortArrow(
    CDC* pDC,  
    CRect rectArrow);
```  
  
### <a name="parameters"></a>參數  
 [in]*pDC*  
 裝置內容的指標。  
  
 [in]*rectArrow*  
 排序箭號的週框。  
  
##  <a name="onfillbackground"></a>  CMFCHeaderCtrl::OnFillBackground  
 標頭控制資料行的背景填滿架構呼叫。  
  
```  
virtual void OnFillBackground(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in]*pDC*  
 裝置內容的指標。  
  
### <a name="remarks"></a>備註  
  
##  <a name="removesortcolumn"></a>  CMFCHeaderCtrl::RemoveSortColumn  
 排序資料行清單中移除指定的資料行。  
  
```  
void RemoveSortColumn(int iColumn);
```  
  
### <a name="parameters"></a>參數  
 [in]*iColumn*  
 若要移除的資料行以零為起始的索引。  
  
##  <a name="setsortcolumn"></a>  CMFCHeaderCtrl::SetSortColumn  
 設定控制項中的指定資料行的排序次序。  
  
```  
void SetSortColumn(
    int iColumn,  
    BOOL bAscending=TRUE,  
    BOOL bAdd=FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in]*iColumn*  
 標頭控制項的資料行以零為起始的索引。 如果這個參數小於零，則這個方法會移除所有資料行的排序資料行清單中。  
  
 [in]*bAscending*  
 指定資料行的排序次序， *iColumn*參數指定。 `TRUE` 若要設定遞增的順序。`FALSE`設遞減的順序。 預設值是 `TRUE`。  
  
 [in]*bAdd*  
 `TRUE` 若要設定資料行的排序次序*iColumn*參數指定。  
  
 如果目前的標頭控制項在*多個資料行排序*模式中，這個方法會將指定的資料行加入至排序資料行的清單。 使用[CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort)設定多個資料行排序模式。  
  
 如果未設定多個資料行排序模式，而且這個方法會編譯偵錯模式中，這個方法會判斷提示。 如果未設定多個資料行排序模式，且這個方法在零售模式中編譯，這個方法會先移除所有資料行排序資料行清單，並將其指定之資料行加入清單。  
  
 `FALSE` 為第一個排序資料行清單中移除所有資料行，然後將指定的資料行加入至清單。 預設值是 `FALSE`。  
  
### <a name="remarks"></a>備註  
 若要設定資料行的排序順序中使用這個方法。 如有必要，這個方法會加入資料行的排序資料行清單。 標題控制項繪製排序箭號，指向向上或向下使用的排序順序。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCListCtrl 類別](../../mfc/reference/cmfclistctrl-class.md)
