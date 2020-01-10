---
title: CMFCRibbonEdit 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::CanBeStretched
- AFXRIBBONEDIT/CMFCRibbonEdit::CopyFrom
- AFXRIBBONEDIT/CMFCRibbonEdit::CreateEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::DestroyCtrl
- AFXRIBBONEDIT/CMFCRibbonEdit::DropDownList
- AFXRIBBONEDIT/CMFCRibbonEdit::EnableSpinButtons
- AFXRIBBONEDIT/CMFCRibbonEdit::GetCompactSize
- AFXRIBBONEDIT/CMFCRibbonEdit::GetEditText
- AFXRIBBONEDIT/CMFCRibbonEdit::GetIntermediateSize
- AFXRIBBONEDIT/CMFCRibbonEdit::GetTextAlign
- AFXRIBBONEDIT/CMFCRibbonEdit::GetWidth
- AFXRIBBONEDIT/CMFCRibbonEdit::HasCompactMode
- AFXRIBBONEDIT/CMFCRibbonEdit::HasFocus
- AFXRIBBONEDIT/CMFCRibbonEdit::HasLargeMode
- AFXRIBBONEDIT/CMFCRibbonEdit::HasSpinButtons
- AFXRIBBONEDIT/CMFCRibbonEdit::IsHighlighted
- AFXRIBBONEDIT/CMFCRibbonEdit::OnAfterChangeRect
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDraw
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDrawLabelAndImage
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDrawOnList
- AFXRIBBONEDIT/CMFCRibbonEdit::OnEnable
- AFXRIBBONEDIT/CMFCRibbonEdit::OnHighlight
- AFXRIBBONEDIT/CMFCRibbonEdit::OnKey
- AFXRIBBONEDIT/CMFCRibbonEdit::OnLButtonDown
- AFXRIBBONEDIT/CMFCRibbonEdit::OnLButtonUp
- AFXRIBBONEDIT/CMFCRibbonEdit::OnRTLChanged
- AFXRIBBONEDIT/CMFCRibbonEdit::OnShow
- AFXRIBBONEDIT/CMFCRibbonEdit::Redraw
- AFXRIBBONEDIT/CMFCRibbonEdit::SetACCData
- AFXRIBBONEDIT/CMFCRibbonEdit::SetEditText
- AFXRIBBONEDIT/CMFCRibbonEdit::SetTextAlign
- AFXRIBBONEDIT/CMFCRibbonEdit::SetWidth
helpviewer_keywords:
- CMFCRibbonEdit [MFC], CMFCRibbonEdit
- CMFCRibbonEdit [MFC], CanBeStretched
- CMFCRibbonEdit [MFC], CMFCRibbonEdit
- CMFCRibbonEdit [MFC], CopyFrom
- CMFCRibbonEdit [MFC], CreateEdit
- CMFCRibbonEdit [MFC], DestroyCtrl
- CMFCRibbonEdit [MFC], DropDownList
- CMFCRibbonEdit [MFC], EnableSpinButtons
- CMFCRibbonEdit [MFC], GetCompactSize
- CMFCRibbonEdit [MFC], GetEditText
- CMFCRibbonEdit [MFC], GetIntermediateSize
- CMFCRibbonEdit [MFC], GetTextAlign
- CMFCRibbonEdit [MFC], GetWidth
- CMFCRibbonEdit [MFC], HasCompactMode
- CMFCRibbonEdit [MFC], HasFocus
- CMFCRibbonEdit [MFC], HasLargeMode
- CMFCRibbonEdit [MFC], HasSpinButtons
- CMFCRibbonEdit [MFC], IsHighlighted
- CMFCRibbonEdit [MFC], OnAfterChangeRect
- CMFCRibbonEdit [MFC], OnDraw
- CMFCRibbonEdit [MFC], OnDrawLabelAndImage
- CMFCRibbonEdit [MFC], OnDrawOnList
- CMFCRibbonEdit [MFC], OnEnable
- CMFCRibbonEdit [MFC], OnHighlight
- CMFCRibbonEdit [MFC], OnKey
- CMFCRibbonEdit [MFC], OnLButtonDown
- CMFCRibbonEdit [MFC], OnLButtonUp
- CMFCRibbonEdit [MFC], OnRTLChanged
- CMFCRibbonEdit [MFC], OnShow
- CMFCRibbonEdit [MFC], Redraw
- CMFCRibbonEdit [MFC], SetACCData
- CMFCRibbonEdit [MFC], SetEditText
- CMFCRibbonEdit [MFC], SetTextAlign
- CMFCRibbonEdit [MFC], SetWidth
ms.assetid: 9b85f1f2-446b-454e-9af9-104fdad8a897
ms.openlocfilehash: 4f973074fbec3d04b1c1a74852b02ff2564217c1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504954"
---
# <a name="cmfcribbonedit-class"></a>CMFCRibbonEdit 類別

執行位於功能區列上的編輯控制項。

## <a name="syntax"></a>語法

```
class CMFCRibbonEdit : public CMFCRibbonButton
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|建構 `CMFCRibbonEdit` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCRibbonEdit::CanBeStretched](#canbestretched)|指出`CMFCRibbonEdit`控制項的高度是否可以垂直增加至功能區資料列的高度。|
|[CMFCRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|建構 `CMFCRibbonEdit` 物件。|
|[CMFCRibbonEdit::CopyFrom](#copyfrom)|將指定`CMFCRibbonEdit`之物件的狀態複製到目前`CMFCRibbonEdit`的物件。|
|[CMFCRibbonEdit::CreateEdit](#createedit)|為`CMFCRibbonEdit`物件建立新的文字方塊。|
|[CMFCRibbonEdit::DestroyCtrl](#destroyctrl)|`CMFCRibbonEdit`終結物件。|
|[CMFCRibbonEdit::DropDownList](#dropdownlist)|下拉式清單方塊。|
|[CMFCRibbonEdit::EnableSpinButtons](#enablespinbuttons)|啟用和設定文字方塊的微調按鈕範圍。|
|[CMFCRibbonEdit::GetCompactSize](#getcompactsize)|抓取`CFMCRibbonEdit`物件的壓縮大小。|
|[CMFCRibbonEdit::GetEditText](#getedittext)|抓取文字方塊中的文字。|
|[CMFCRibbonEdit::GetIntermediateSize](#getintermediatesize)|抓取`CMFCRibbonEdit`物件的中繼大小。|
|[CMFCRibbonEdit::GetTextAlign](#gettextalign)|抓取文字方塊中的文字對齊方式。|
|[CMFCRibbonEdit::GetWidth](#getwidth)|抓取`CMFCRibbonEdit`控制項的寬度（以圖元為單位）。|
|[CMFCRibbonEdit::HasCompactMode](#hascompactmode)|指出`CMFCRibbonEdit`控制項的顯示大小是否可以精簡。|
|[CMFCRibbonEdit::HasFocus](#hasfocus)|指出`CMFCRIbbonEdit`控制項是否具有焦點。|
|[CMFCRibbonEdit::HasLargeMode](#haslargemode)|指出`CMFCRibbonEdit`控制項的顯示大小是否會很大。|
|[CMFCRibbonEdit::HasSpinButtons](#hasspinbuttons)|指出文字方塊是否有微調按鈕。|
|[CMFCRibbonEdit::IsHighlighted](#ishighlighted)|指出是否`CMFCRibbonEdit`反白顯示控制項。|
|[CMFCRibbonEdit::OnAfterChangeRect](#onafterchangerect)|當`CMFCRibbonEdit`控制項的顯示矩形維度變更時由架構呼叫。|
|[CMFCRibbonEdit::OnDraw](#ondraw)|由架構呼叫以繪製`CMFCRibbonEdit`控制項。|
|[CMFCRibbonEdit::OnDrawLabelAndImage](#ondrawlabelandimage)|由架構呼叫以繪製`CMFCRibbonEdit`控制項的標籤和影像。|
|[CMFCRibbonEdit::OnDrawOnList](#ondrawonlist)|由架構呼叫，以在 [ `CMFCRibbonEdit`命令] 清單方塊中繪製控制項。|
|[CMFCRibbonEdit::OnEnable](#onenable)|由架構呼叫以啟用或停`CMFCRibbonEdit`用控制項。|
|[CMFCRibbonEdit::OnHighlight](#onhighlight)|當指標進入或離開`CMFCRibbonEdit`控制項的邊界時，由架構呼叫。|
|[CMFCRibbonEdit::OnKey](#onkey)|當使用者按下 keytip 且`CMFCRibbonEdit`控制項具有焦點時，由架構呼叫。|
|[CMFCRibbonEdit::OnLButtonDown](#onlbuttondown)|當使用者在控制項上按下`CMFCRibbonEdit`滑鼠左鍵時，由架構呼叫以更新控制項。|
|[CMFCRibbonEdit::OnLButtonUp](#onlbuttonup)|當使用者放開滑鼠左鍵時由架構呼叫。|
|[CMFCRibbonEdit::OnRTLChanged](#onrtlchanged)|當版面配置變更方向時， `CMFCRibbonEdit`由架構呼叫以更新控制項。|
|[CMFCRibbonEdit::OnShow](#onshow)|由架構呼叫以顯示或隱藏`CMFCRibbonEdit`控制項。|
|[CMFCRibbonEdit::Redraw](#redraw)|更新`CMFCRibbonEdit`控制項的顯示。|
|[CMFCRibbonEdit::SetACCData](#setaccdata)|設定`CMFCRibbonEdit`物件的協助工具資料。|
|[CMFCRibbonEdit::SetEditText](#setedittext)|設定文字方塊中的文字。|
|[CMFCRibbonEdit::SetTextAlign](#settextalign)|設定文字方塊的文字對齊方式。|
|[CMFCRibbonEdit::SetWidth](#setwidth)|設定`CMFCRibbonEdit`控制項文字方塊的寬度。|

## <a name="remarks"></a>備註

## <a name="example"></a>範例

下列範例示範如何建立`CMFCRibbonEdit`物件、在編輯控制項旁顯示微調按鈕，以及設定編輯控制項的文字。 此程式碼片段是[MS Office 2007 示範範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_MSOffice2007Demo#7](../../mfc/reference/codesnippet/cpp/cmfcribbonedit-class_1.cpp)]

## <a name="requirements"></a>需求

**標頭：** afxRibbonEdit。h

##  <a name="canbestretched"></a>CMFCRibbonEdit::CanBeStretched

指出[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項的高度是否可以垂直增加至功能區資料列的高度。

```
virtual BOOL CanBeStretched();
```

### <a name="return-value"></a>傳回值

一律傳回 FALSE。

### <a name="remarks"></a>備註

##  <a name="cmfcribbonedit"></a>CMFCRibbonEdit::CMFCRibbonEdit

結構[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)物件。

```
CMFCRibbonEdit(
    UINT nID,
    int nWidth,
    LPCTSTR lpszLabel = NULL,
    int nImage = -1);

CMFCRibbonEdit();
```

### <a name="parameters"></a>參數

*nID*<br/>
在控制項的`CMFCRibbonEdit`命令識別碼。

*nWidth*<br/>
在`CMFCRibbonEdit`控制項文字方塊的寬度（以圖元為單位）。

*lpszLabel*<br/>
在`CMFCRibbonEdit`控制項的標籤。

*nImage*<br/>
在要`CMFCRibbonEdit`用於控制項的小型影像索引。 小型影像的集合是由父功能區分類所維護。

### <a name="remarks"></a>備註

`CMFCRibbonEdit`控制項不會使用大型影像。

##  <a name="copyfrom"></a>CMFCRibbonEdit：： CopyFrom

將指定之[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)物件的狀態複製到目前的[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)物件。

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>參數

*src*<br/>
在來源`CMFCRibbonEdit`物件。

### <a name="remarks"></a>備註

*Src*參數的類型`CMFCRibbonEdit`必須是。

##  <a name="createedit"></a>CMFCRibbonEdit::CreateEdit

建立[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)物件的新文字方塊。

```
virtual CMFCRibbonRichEditCtrl* CreateEdit(
    CWnd* pWndParent,
    DWORD dwEditStyle);
```

### <a name="parameters"></a>參數

*pWndParent*<br/>
在`CMFCRibbonEdit`物件之父視窗的指標。

*dwEditStyle*<br/>
在指定文字方塊的樣式。 您可以結合 [備註] 區段中所列的視窗樣式與 Windows SDK 中所述的[編輯控制項樣式](/windows/win32/Controls/edit-control-styles)。

### <a name="return-value"></a>傳回值

如果方法成功，則為新文字方塊的指標;否則為 Null。

### <a name="remarks"></a>備註

覆寫衍生類別中的這個方法，以建立自訂文字方塊。

您可以將下列[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)套用至文字方塊：

- **WS_CHILD**

- **WS_VISIBLE**

- **WS_DISABLED**

- **WS_GROUP**

- **WS_TABSTOP**

##  <a name="destroyctrl"></a>CMFCRibbonEdit：:D estroyCtrl

終結[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)物件。

```
virtual void DestroyCtrl();
```

### <a name="remarks"></a>備註

##  <a name="dropdownlist"></a>CMFCRibbonEdit：:D ropDownList

下拉式清單方塊。

```
virtual void DropDownList();
```

### <a name="remarks"></a>備註

根據預設，此方法不會執行任何操作。 覆寫此方法以下拉式清單方塊。

##  <a name="enablespinbuttons"></a>CMFCRibbonEdit::EnableSpinButtons

啟用和設定文字方塊的微調按鈕範圍。

```
void EnableSpinButtons(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>參數

*nMin*<br/>
在微調按鈕的最小值。

*nMax*<br/>
在微調按鈕的最大值。

### <a name="remarks"></a>備註

微調按鈕會顯示向上和向下箭號，並可讓使用者在一組固定值之間移動。

##  <a name="getcompactsize"></a>CMFCRibbonEdit：： GetCompactSize

抓取[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)物件的壓縮大小。

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
在`CMFCRibbonEdit`物件之裝置內容的指標。

### <a name="return-value"></a>傳回值

`CMFCRibbonEdit`物件的壓縮大小。

### <a name="remarks"></a>備註

##  <a name="getedittext"></a>CMFCRibbonEdit::GetEditText

抓取文字方塊中的文字。

```
CString GetEditText() const;
```

### <a name="return-value"></a>傳回值

文字方塊中的文字。

### <a name="remarks"></a>備註

##  <a name="getintermediatesize"></a>CMFCRibbonEdit：： GetIntermediateSize

抓取[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)物件的中繼大小。

```
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
在`CMFCRibbonEdit`物件之裝置內容的指標。

### <a name="return-value"></a>傳回值

`CMFCRibbonEdit`物件的中繼大小。

### <a name="remarks"></a>備註

##  <a name="gettextalign"></a>CMFCRibbonEdit::GetTextAlign

抓取文字方塊中的文字對齊方式。

```
int GetTextAlign() const;
```

### <a name="return-value"></a>傳回值

文字對齊列舉值。 如需可能的值，請參閱備註一節。

### <a name="remarks"></a>備註

傳回的值是下列其中一個編輯控制項樣式：

- 左對齊的**ES_LEFT**

- 置中對齊的**ES_CENTER**

- 靠右對齊的**ES_RIGHT**

如需這些樣式的詳細資訊，請參閱[編輯控制項樣式](/windows/win32/Controls/edit-control-styles)。

##  <a name="getwidth"></a>CMFCRibbonEdit::GetWidth

抓取[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項的寬度（以圖元為單位）。

```
int GetWidth(BOOL bInFloatyMode = FALSE) const;
```

### <a name="parameters"></a>參數

*bInFloatyMode*<br/>
在如果`CMFCRibbonEdit`控制項處於浮動模式，則為 TRUE，否則為 FALSE。

### <a name="return-value"></a>傳回值

`CMFCRibbonEdit`控制項的寬度（以圖元為單位）。

### <a name="remarks"></a>備註

##  <a name="hascompactmode"></a>CMFCRibbonEdit::HasCompactMode

指出[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項的顯示大小是否可以精簡。

```
virtual BOOL HasCompactMode() const;
```

### <a name="return-value"></a>傳回值

一律傳回 TRUE。

### <a name="remarks"></a>備註

根據預設，這個方法一律會傳回 TRUE。 覆寫這個方法，以指出顯示大小是否可以精簡。

##  <a name="hasfocus"></a>CMFCRibbonEdit::HasFocus

指出[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項是否具有焦點。

```
virtual BOOL HasFocus() const;
```

### <a name="return-value"></a>傳回值

如果`CMFCRibbonEdit`控制項具有焦點，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="haslargemode"></a>CMFCRibbonEdit::HasLargeMode

指出[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項的顯示大小是否可能很大。

```
virtual BOOL HasLargeMode() const;
```

### <a name="return-value"></a>傳回值

一律傳回 FALSE。

### <a name="remarks"></a>備註

根據預設，這個方法一律會傳回 FALSE。 覆寫這個方法，以指出顯示大小是否可以很大。

##  <a name="hasspinbuttons"></a>CMFCRibbonEdit::HasSpinButtons

指出文字方塊是否有微調按鈕。

```
virtual BOOL HasSpinButtons() const;
```

### <a name="return-value"></a>傳回值

如果文字方塊具有微調按鈕，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="ishighlighted"></a>CMFCRibbonEdit::IsHighlighted

指出是否反白顯示[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項。

```
virtual BOOL IsHighlighted() const;
```

### <a name="return-value"></a>傳回值

如果已反`CMFCRibbonEdit`白顯示控制項，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="onafterchangerect"></a>CMFCRibbonEdit::OnAfterChangeRect

當[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項的顯示矩形尺寸變更時由架構呼叫。

```
virtual void OnAfterChangeRect(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
在`CMFCRibbonEdit`控制項之裝置內容的指標。

### <a name="remarks"></a>備註

##  <a name="ondraw"></a>CMFCRibbonEdit：： OnDraw

由架構呼叫以繪製[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
在`CMFCRibbonEdit`控制項之裝置內容的指標。

### <a name="remarks"></a>備註

##  <a name="ondrawlabelandimage"></a>CMFCRibbonEdit::OnDrawLabelAndImage

由架構呼叫，以繪製[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項的標籤和影像。

```
virtual void OnDrawLabelAndImage(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
在`CMFCRibbonEdit`控制項之裝置內容的指標。

### <a name="remarks"></a>備註

##  <a name="ondrawonlist"></a>CMFCRibbonEdit::OnDrawOnList

由架構呼叫，以在 [命令] 清單方塊中繪製[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項。

```
virtual void OnDrawOnList(
    CDC* pDC,
    CString strText,
    int nTextOffset,
    CRect rect,
    BOOL bIsSelected,
    BOOL bHighlighted);
```

### <a name="parameters"></a>參數

*pDC*<br/>
在`CMFCRibbonEdit`控制項之裝置內容的指標。

*strText*<br/>
在顯示文字[] (../../mfc/reference/cmfcribbonedit-class.md "cmfcribbonedit 類別")。

*nTextOffset*<br/>
在從清單方塊左邊到顯示文字的距離（以圖元為單位）。

*rect*<br/>
在`CMFCRibbonEdit`控制項的顯示矩形。

*bIsSelected*<br/>
在不使用這個參數。

*bHighlighted*<br/>
在不使用這個參數。

### <a name="remarks"></a>備註

[命令] 清單方塊會顯示功能區控制項，讓使用者自訂快速存取工具列。

##  <a name="onenable"></a>CMFCRibbonEdit::OnEnable

由架構呼叫以啟用或停用[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項。

```
virtual void OnEnable(BOOL bEnable);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
在TRUE 表示啟用控制項;FALSE 表示停用控制項。

### <a name="remarks"></a>備註

##  <a name="onhighlight"></a>CMFCRibbonEdit::OnHighlight

當指標進入或離開[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項的界限時，由架構呼叫。

```
virtual void OnHighlight(BOOL bHighlight);
```

### <a name="parameters"></a>參數

*bHighlight*<br/>
在如果指標位於`CMFCRibbonEdit`控制項的界限，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="onkey"></a>CMFCRibbonEdit::OnKey

當使用者按下 keytip，而且[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項有焦點時，由架構呼叫。

```
virtual BOOL OnKey(BOOL bIsMenuKey);
```

### <a name="parameters"></a>參數

*bIsMenuKey*<br/>
在如果 keytip 顯示快顯功能表，則為 TRUE;否則為 FALSE。

### <a name="return-value"></a>傳回值

如果事件已處理，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="onlbuttondown"></a>CMFCRibbonEdit::OnLButtonDown

當使用者在控制項上按下滑鼠左鍵時，由架構呼叫以更新[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項。

```
virtual void OnLButtonDown(CPoint point);
```

### <a name="parameters"></a>參數

*point*<br/>
在不使用這個參數。

### <a name="remarks"></a>備註

##  <a name="onlbuttonup"></a>CMFCRibbonEdit::OnLButtonUp

當使用者放開滑鼠左鍵時由架構呼叫。

```
virtual void OnLButtonUp(CPoint point);
```

### <a name="parameters"></a>參數

*point*<br/>
在不使用這個參數。

### <a name="remarks"></a>備註

##  <a name="onrtlchanged"></a>CMFCRibbonEdit::OnRTLChanged

當版面配置變更方向時，由架構呼叫以更新[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項。

```
virtual void OnRTLChanged(BOOL bIsRTL);
```

### <a name="parameters"></a>參數

*bIsRTL*<br/>
在如果版面配置是由右至左，則為 TRUE;若版面配置為從左至右，則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="onshow"></a>CMFCRibbonEdit::OnShow

由架構呼叫以顯示或隱藏[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項。

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>參數

*bShow*<br/>
在TRUE 表示顯示控制項;FALSE 表示隱藏控制項。

### <a name="remarks"></a>備註

##  <a name="redraw"></a>CMFCRibbonEdit：：重繪

更新[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項的顯示。

```
virtual void Redraw();
```

### <a name="remarks"></a>備註

這個方法會透過間接呼叫`CMFCRibbonEdit` [CWnd：： RedrawWindow](/windows/win32/api/winuser/nf-winuser-redrawwindow)並設定 RDW_INVALIDATE、RDW_ERASE 和 RDW_UPDATENOW 旗標，來重新繪製物件的顯示矩形。

##  <a name="setaccdata"></a>CMFCRibbonEdit：： SetACCData

設定[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)物件的協助工具資料。

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>參數

*pParent*<br/>
`CMFCRibbonEdit`物件之父視窗的指標。

*data*<br/>
`CMFCRibbonEdit`物件的協助工具資料。

### <a name="return-value"></a>傳回值

一律傳回 TRUE。

### <a name="remarks"></a>備註

##  <a name="setedittext"></a>CMFCRibbonEdit::SetEditText

設定文字方塊中的文字。

```
void SetEditText(CString strText);
```

### <a name="parameters"></a>參數

*strText*<br/>
在文字方塊的文字。

##  <a name="settextalign"></a>CMFCRibbonEdit::SetTextAlign

設定文字方塊的文字對齊方式。

```
void SetTextAlign(int nAlign);
```

### <a name="parameters"></a>參數

*nAlign*<br/>
在文字對齊列舉值。 如需可能的值，請參閱備註一節。

### <a name="remarks"></a>備註

參數*nAlign*是下列其中一個編輯控制項樣式：

- 左對齊的 ES_LEFT

- 置中對齊的 ES_CENTER

- 靠右對齊的 ES_RIGHT

如需這些樣式的詳細資訊，請參閱[編輯控制項樣式](/windows/win32/Controls/edit-control-styles)。

##  <a name="setwidth"></a>CMFCRibbonEdit::SetWidth

設定[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項文字方塊的寬度。

```
void SetWidth(
    int nWidth,
    BOOL bInFloatyMode = FALSE);
```

### <a name="parameters"></a>參數

*nWidth*<br/>
在文字方塊的寬度（以圖元為單位）。

*bInFloatyMode*<br/>
TRUE 表示設定浮動模式的寬度;FALSE 表示設定標準模式的寬度。

### <a name="remarks"></a>備註

`CMFCRibbonEdit`控制項有兩個寬度，視其顯示模式而定：浮動模式和一般模式。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton 類別](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[CMFCRibbonBar 類別](../../mfc/reference/cmfcribbonbar-class.md)
