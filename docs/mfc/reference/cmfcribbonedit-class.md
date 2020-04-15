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
ms.openlocfilehash: ab621a05f9b658eee9babb14e257680fa95e0f96
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375184"
---
# <a name="cmfcribbonedit-class"></a>CMFCRibbonEdit 類別

實現位於功能區列上的編輯控制項。

## <a name="syntax"></a>語法

```cpp
class CMFCRibbonEdit : public CMFCRibbonButton
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFC 剪彩編輯:CMFC 剪綵編輯](#cmfcribbonedit)|建構 `CMFCRibbonEdit` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFC 剪彩編輯:可拉伸](#canbestretched)|指示`CMFCRibbonEdit`控項是否可以垂直增加到功能區行的高度。|
|[CMFC 剪彩編輯:CMFC 剪綵編輯](#cmfcribbonedit)|建構 `CMFCRibbonEdit` 物件。|
|[CMFC 剪彩編輯::從](#copyfrom)|將指定`CMFCRibbonEdit`物件的狀態複製到`CMFCRibbonEdit`當前 物件。|
|[CMFC 功能編輯:建立編輯](#createedit)|為`CMFCRibbonEdit`物件創建新的文字框。|
|[CMFC剪髮編輯::D](#destroyctrl)|銷毀`CMFCRibbonEdit`物件。|
|[CMFC 功能編輯::DropDownlist](#dropdownlist)|下一個清單框。|
|[CMFC 功能編輯::開啟旋轉按鈕](#enablespinbuttons)|啟用並設置文本框的旋轉按鈕的範圍。|
|[CMFC 功能編輯:取得壓縮大小](#getcompactsize)|檢索`CFMCRibbonEdit`物件的緊湊大小。|
|[CMFC 功能編輯:取得編輯文字](#getedittext)|檢索文字框中的文字。|
|[CMFC 功能編輯:取得中間大小](#getintermediatesize)|檢索`CMFCRibbonEdit`物件的中間大小。|
|[CMFC 功能編輯:取得文字對齊](#gettextalign)|檢索文字框中文字的對齊方式。|
|[CMFC 功能編輯:取得寬度](#getwidth)|檢索`CMFCRibbonEdit`控件的寬度(以像素為單位)。|
|[CMFC 功能編輯::具有壓縮模式](#hascompactmode)|指示`CMFCRibbonEdit`控件的顯示大小是否可以緊湊。|
|[CMFC 功能編輯::有焦點](#hasfocus)|指示`CMFCRIbbonEdit`控件是否具有焦點。|
|[CMFC 功能編輯:具有大型模式](#haslargemode)|指示`CMFCRibbonEdit`控制項的顯示大小是否可以很大。|
|[CMFC 功能編輯::哈斯平按鈕](#hasspinbuttons)|指示文本框是否具有旋轉按鈕。|
|[CMFC 功能編輯:已突顯](#ishighlighted)|指示`CMFCRibbonEdit`控件是否突出顯示。|
|[CMFC 剪經:在轉換後](#onafterchangerect)|當`CMFCRibbonEdit`控件的顯示矩形的尺寸發生更改時,由框架調用。|
|[CMFC 剪彩編輯:OnDraw](#ondraw)|由框架調用以繪製`CMFCRibbonEdit`控制件。|
|[CMFC 剪貼畫:畫條和圖像](#ondrawlabelandimage)|由框架調用以繪製`CMFCRibbonEdit`控制件的標籤和圖像。|
|[CMFC 剪彩編輯:在畫上清單](#ondrawonlist)|由框架呼叫以`CMFCRibbonEdit`在命令清單框中繪製控制件。|
|[CMFC 剪彩編輯:開啟](#onenable)|由框架調用以啟用或禁用`CMFCRibbonEdit`控制項。|
|[CMFC 剪彩編輯::上高亮顯示](#onhighlight)|當指標進入或離開`CMFCRibbonEdit`控件的邊界時,由框架調用。|
|[CMFC 剪彩編輯::打開鍵](#onkey)|當使用者按下鍵尖並且`CMFCRibbonEdit`控件具有焦點時,由框架調用。|
|[CMFC 剪彩編輯::打開按鈕](#onlbuttondown)|當使用者按下控制件上的滑鼠左鍵`CMFCRibbonEdit`時,框架調用以更新控制項。|
|[CMFC 剪接編輯::OnLButtonUp](#onlbuttonup)|當用戶釋放滑鼠左鍵時由框架調用。|
|[CMFC 剪彩編輯::開啟](#onrtlchanged)|由框架呼叫,`CMFCRibbonEdit`以在佈局更改方向時更新控制項。|
|[CMFC 剪綵編輯:在展會上](#onshow)|由框架呼叫以顯示或隱藏`CMFCRibbonEdit`控制項。|
|[CMFC 剪彩編輯:重繪](#redraw)|更新控制項的`CMFCRibbonEdit`顯示。|
|[CMFC 功能編輯:設定ACC資料](#setaccdata)|設置`CMFCRibbonEdit`物件的輔助功能數據。|
|[CMFC 功能編輯::設定編輯文字](#setedittext)|在文字框中設定文本。|
|[CMFC 剪彩編輯::設定文字對齊](#settextalign)|設定文字框的文字對齊方式。|
|[CMFC 功能編輯::設定寬度](#setwidth)|設置控制項的文字框的`CMFCRibbonEdit`寬度。|

## <a name="remarks"></a>備註

## <a name="example"></a>範例

下面的範例展示如何建構`CMFCRibbonEdit`物件、在編輯控制項旁邊顯示旋轉按鈕以及設置編輯控制件的文本。 此代碼段是 MS [Office 2007 演示範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_MSOffice2007Demo#7](../../mfc/reference/codesnippet/cpp/cmfcribbonedit-class_1.cpp)]

## <a name="requirements"></a>需求

**標題:** afxRibbonEdit.h

## <a name="cmfcribboneditcanbestretched"></a><a name="canbestretched"></a>CMFC 剪彩編輯:可拉伸

指示[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制件的高度是否可以垂直增加到功能區行的高度。

```cpp
virtual BOOL CanBeStretched();
```

### <a name="return-value"></a>傳回值

始終返回 FALSE。

### <a name="remarks"></a>備註

## <a name="cmfcribboneditcmfcribbonedit"></a><a name="cmfcribbonedit"></a>CMFC 剪彩編輯:CMFC 剪綵編輯

建構[CMFC 功能編輯](../../mfc/reference/cmfcribbonedit-class.md)物件。

```cpp
CMFCRibbonEdit(
    UINT nID,
    int nWidth,
    LPCTSTR lpszLabel = NULL,
    int nImage = -1);

CMFCRibbonEdit();
```

### <a name="parameters"></a>參數

*nID*<br/>
[在]控件的命令`CMFCRibbonEdit`識別碼。

*n 寬度*<br/>
[在]`CMFCRibbonEdit`控件的文字框的寬度(以像素為單位)。

*lpszLabel*<br/>
[在]控制項標籤`CMFCRibbonEdit`。

*n 影像*<br/>
[在]用於控制的影像的`CMFCRibbonEdit`索引。 小圖像的集合由父功能區類別維護。

### <a name="remarks"></a>備註

控件`CMFCRibbonEdit`不使用大圖像。

## <a name="cmfcribboneditcopyfrom"></a><a name="copyfrom"></a>CMFC 剪彩編輯::從

將指定的[CMFC 功能編輯](../../mfc/reference/cmfcribbonedit-class.md)物件的狀態複製到當前[CMFC 功能編輯](../../mfc/reference/cmfcribbonedit-class.md)物件。

```cpp
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>參數

*src*<br/>
[在]源`CMFCRibbonEdit`物件。

### <a name="remarks"></a>備註

*src*參數的類型`CMFCRibbonEdit`必須為 。

## <a name="cmfcribboneditcreateedit"></a><a name="createedit"></a>CMFC 功能編輯:建立編輯

為[CMFC 功能編輯](../../mfc/reference/cmfcribbonedit-class.md)物件創建新的文本框。

```cpp
virtual CMFCRibbonRichEditCtrl* CreateEdit(
    CWnd* pWndParent,
    DWORD dwEditStyle);
```

### <a name="parameters"></a>參數

*pwnd 父級*<br/>
[在]指向物件的父視窗的`CMFCRibbonEdit`指標。

*dwEdit 風格*<br/>
[在]指定文字框的樣式。 您可以將「備註」部分中列出的視窗樣式與 Windows SDK 中描述的[編輯控制件樣式](/windows/win32/Controls/edit-control-styles)相結合。

### <a name="return-value"></a>傳回值

如果方法成功,則指向新文本框的指標;否則,NULL。

### <a name="remarks"></a>備註

重寫派生類中的此方法以創建自定義文本框。

您可以將以下[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)套用於文字盒:

- **WS_CHILD**

- **WS_VISIBLE**

- **WS_DISABLED**

- **WS_GROUP**

- **WS_TABSTOP**

## <a name="cmfcribboneditdestroyctrl"></a><a name="destroyctrl"></a>CMFC剪髮編輯::D

銷毀[CMFC 功能編輯](../../mfc/reference/cmfcribbonedit-class.md)物件。

```cpp
virtual void DestroyCtrl();
```

### <a name="remarks"></a>備註

## <a name="cmfcribboneditdropdownlist"></a><a name="dropdownlist"></a>CMFC 功能編輯::DropDownlist

下一個清單框。

```cpp
virtual void DropDownList();
```

### <a name="remarks"></a>備註

默認情況下,此方法不執行任何操作。 重寫此方法以下拉列表框。

## <a name="cmfcribboneditenablespinbuttons"></a><a name="enablespinbuttons"></a>CMFC 功能編輯::開啟旋轉按鈕

啟用並設置文本框的旋轉按鈕的範圍。

```cpp
void EnableSpinButtons(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>參數

*nMin*<br/>
[在]旋轉按鈕的最小值。

*nMax*<br/>
[在]旋轉按鈕的最大值。

### <a name="remarks"></a>備註

旋轉按鈕顯示向上和向下箭頭,使用戶能夠通過一組固定的值移動。

## <a name="cmfcribboneditgetcompactsize"></a><a name="getcompactsize"></a>CMFC 功能編輯:取得壓縮大小

檢索[CMFC 功能編輯](../../mfc/reference/cmfcribbonedit-class.md)物件的緊湊大小。

```cpp
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向`CMFCRibbonEdit`物件的設備上下文。

### <a name="return-value"></a>傳回值

`CMFCRibbonEdit`對象的緊湊大小。

### <a name="remarks"></a>備註

## <a name="cmfcribboneditgetedittext"></a><a name="getedittext"></a>CMFC 功能編輯:取得編輯文字

檢索文字框中的文字。

```cpp
CString GetEditText() const;
```

### <a name="return-value"></a>傳回值

文字框中的文字。

### <a name="remarks"></a>備註

## <a name="cmfcribboneditgetintermediatesize"></a><a name="getintermediatesize"></a>CMFC 功能編輯:取得中間大小

檢索[CMFC 功能編輯](../../mfc/reference/cmfcribbonedit-class.md)物件的中間大小。

```cpp
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向`CMFCRibbonEdit`物件的設備上下文。

### <a name="return-value"></a>傳回值

`CMFCRibbonEdit`對象的中間大小。

### <a name="remarks"></a>備註

## <a name="cmfcribboneditgettextalign"></a><a name="gettextalign"></a>CMFC 功能編輯:取得文字對齊

檢索文字框中文字的對齊方式。

```cpp
int GetTextAlign() const;
```

### <a name="return-value"></a>傳回值

文字對齊枚舉值。 有關可能的值,請參閱備註部分。

### <a name="remarks"></a>備註

傳回的值是以下編輯控制項樣式之一:

- **用於**左對齊ES_LEFT

- **用於中心對齊的ES_CENTER**

- **ES_RIGHT,** 用於正確對齊

有關這些樣式的詳細資訊,請參閱[編輯控制項樣式](/windows/win32/Controls/edit-control-styles)。

## <a name="cmfcribboneditgetwidth"></a><a name="getwidth"></a>CMFC 功能編輯:取得寬度

檢索[CMFC 功能編輯](../../mfc/reference/cmfcribbonedit-class.md)控制項的寬度(以像素為單位)。

```cpp
int GetWidth(BOOL bInFloatyMode = FALSE) const;
```

### <a name="parameters"></a>參數

*bInFloatyMode*<br/>
[在]如果`CMFCRibbonEdit`控件處於浮動模式,則為 TRUE;否則,FALSE。

### <a name="return-value"></a>傳回值

控件的`CMFCRibbonEdit`寬度(以像素為單位)。

### <a name="remarks"></a>備註

## <a name="cmfcribbonedithascompactmode"></a><a name="hascompactmode"></a>CMFC 功能編輯::具有壓縮模式

指示[CMFC 功能編輯](../../mfc/reference/cmfcribbonedit-class.md)控制件的顯示大小是否可以緊湊。

```cpp
virtual BOOL HasCompactMode() const;
```

### <a name="return-value"></a>傳回值

始終返回 TRUE。

### <a name="remarks"></a>備註

默認情況下,此方法始終返回 TRUE。 重寫此方法以指示顯示大小是否可以緊湊。

## <a name="cmfcribbonedithasfocus"></a><a name="hasfocus"></a>CMFC 功能編輯::有焦點

指示[CMFC 功能編輯](../../mfc/reference/cmfcribbonedit-class.md)控件是否有焦點。

```cpp
virtual BOOL HasFocus() const;
```

### <a name="return-value"></a>傳回值

如果控件具有`CMFCRibbonEdit`焦點,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

## <a name="cmfcribbonedithaslargemode"></a><a name="haslargemode"></a>CMFC 功能編輯:具有大型模式

指示[CMFC 功能編輯](../../mfc/reference/cmfcribbonedit-class.md)控件的顯示大小是否較大。

```cpp
virtual BOOL HasLargeMode() const;
```

### <a name="return-value"></a>傳回值

始終返回 FALSE。

### <a name="remarks"></a>備註

默認情況下,此方法始終返回 FALSE。 重寫此方法以指示顯示大小是否可以大。

## <a name="cmfcribbonedithasspinbuttons"></a><a name="hasspinbuttons"></a>CMFC 功能編輯::哈斯平按鈕

指示文本框是否具有旋轉按鈕。

```cpp
virtual BOOL HasSpinButtons() const;
```

### <a name="return-value"></a>傳回值

如果文字框具有旋轉按鈕,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

## <a name="cmfcribboneditishighlighted"></a><a name="ishighlighted"></a>CMFC 功能編輯:已突顯

指示是否突出顯示[了 CMFC 功能編輯](../../mfc/reference/cmfcribbonedit-class.md)控件。

```cpp
virtual BOOL IsHighlighted() const;
```

### <a name="return-value"></a>傳回值

如果控件突出顯示`CMFCRibbonEdit`,則為 TRUE;如果控件突出顯示,則為 TRUE。否則 FALSE。

### <a name="remarks"></a>備註

## <a name="cmfcribboneditonafterchangerect"></a><a name="onafterchangerect"></a>CMFC 剪經:在轉換後

當[CMFC 功能編輯](../../mfc/reference/cmfcribbonedit-class.md)控制件的顯示矩形的尺寸發生更改時,由框架調用。

```cpp
virtual void OnAfterChangeRect(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向`CMFCRibbonEdit`控制項裝置上下文。

### <a name="remarks"></a>備註

## <a name="cmfcribboneditondraw"></a><a name="ondraw"></a>CMFC 剪彩編輯:OnDraw

由框架調用以繪製[CMFC 功能區編輯](../../mfc/reference/cmfcribbonedit-class.md)控制項。

```cpp
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向`CMFCRibbonEdit`控制項裝置上下文。

### <a name="remarks"></a>備註

## <a name="cmfcribboneditondrawlabelandimage"></a><a name="ondrawlabelandimage"></a>CMFC 剪貼畫:畫條和圖像

由框架調用,以繪製[CMFC 功能編輯](../../mfc/reference/cmfcribbonedit-class.md)控制件的標籤和圖像。

```cpp
virtual void OnDrawLabelAndImage(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向`CMFCRibbonEdit`控制項裝置上下文。

### <a name="remarks"></a>備註

## <a name="cmfcribboneditondrawonlist"></a><a name="ondrawonlist"></a>CMFC 剪彩編輯:在畫上清單

由框架呼叫以在指令清單框中繪製[CMFCRibbonEdit 控制項](../../mfc/reference/cmfcribbonedit-class.md)。

```cpp
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
[在]指向`CMFCRibbonEdit`控制項裝置上下文。

*斯特文字*<br/>
[在]顯示文字[](../../mfc/reference/cmfcribbonedit-class.md "cmfcribbonedit 類別")。

*n文字位移*<br/>
[在]從清單框左側到顯示文本的距離(以像素為單位)。

*矩形*<br/>
[在]控制項顯示`CMFCRibbonEdit`矩形。

*bIs 選擇*<br/>
[在]不使用此參數。

*突顯突顯*<br/>
[在]不使用此參數。

### <a name="remarks"></a>備註

命令列表框顯示功能區控制項,使用戶能夠自訂快速存取工具列。

## <a name="cmfcribboneditonenable"></a><a name="onenable"></a>CMFC 剪彩編輯:開啟

由框架呼叫以啟用或禁用[CMFC 功能編輯](../../mfc/reference/cmfcribbonedit-class.md)控制件。

```cpp
virtual void OnEnable(BOOL bEnable);
```

### <a name="parameters"></a>參數

*b 啟用*<br/>
[在]TRUE 以啟用控制項;FALSE 以禁用控制項。

### <a name="remarks"></a>備註

## <a name="cmfcribboneditonhighlight"></a><a name="onhighlight"></a>CMFC 剪彩編輯::上高亮顯示

當指標進入或離開[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控件的邊界時,由框架調用。

```cpp
virtual void OnHighlight(BOOL bHighlight);
```

### <a name="parameters"></a>參數

*b 高光*<br/>
[在]如果指標位於控件的邊界內,`CMFCRibbonEdit`則為 TRUE;如果指標位於控件的邊界內,則為 TRUE。否則,FALSE。

### <a name="remarks"></a>備註

## <a name="cmfcribboneditonkey"></a><a name="onkey"></a>CMFC 剪彩編輯::打開鍵

當使用者按下鑰匙尖和[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控件具有焦點時,由框架調用。

```cpp
virtual BOOL OnKey(BOOL bIsMenuKey);
```

### <a name="parameters"></a>參數

*bIsMenu 鍵*<br/>
[在]如果鑰匙提示顯示彈出式功能表,則為 TRUE;否則,FALSE。

### <a name="return-value"></a>傳回值

如果事件已處理,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

## <a name="cmfcribboneditonlbuttondown"></a><a name="onlbuttondown"></a>CMFC 剪彩編輯::打開按鈕

當使用者按下控制件上的滑鼠左鍵時,框架調用以更新[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制件。

```cpp
virtual void OnLButtonDown(CPoint point);
```

### <a name="parameters"></a>參數

*點*<br/>
[在]不使用此參數。

### <a name="remarks"></a>備註

## <a name="cmfcribboneditonlbuttonup"></a><a name="onlbuttonup"></a>CMFC 剪接編輯::OnLButtonUp

當用戶釋放滑鼠左鍵時由框架調用。

```cpp
virtual void OnLButtonUp(CPoint point);
```

### <a name="parameters"></a>參數

*點*<br/>
[在]不使用此參數。

### <a name="remarks"></a>備註

## <a name="cmfcribboneditonrtlchanged"></a><a name="onrtlchanged"></a>CMFC 剪彩編輯::開啟

當佈局更改方向時,框架調用以更新[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制項。

```cpp
virtual void OnRTLChanged(BOOL bIsRTL);
```

### <a name="parameters"></a>參數

*比塞爾*<br/>
[在]如果佈局從右到左,則為 TRUE;如果佈局從右到左,則為 TRUE。如果佈局從左到右,則 FALSE。

### <a name="remarks"></a>備註

## <a name="cmfcribboneditonshow"></a><a name="onshow"></a>CMFC 剪綵編輯:在展會上

由框架呼叫以顯示或隱藏[CMFC 功能編輯](../../mfc/reference/cmfcribbonedit-class.md)控制項。

```cpp
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>參數

*b 顯示*<br/>
[在]TRUE 以顯示控制項;FALSE 以隱藏控制項。

### <a name="remarks"></a>備註

## <a name="cmfcribboneditredraw"></a><a name="redraw"></a>CMFC 剪彩編輯:重繪

更新[CMFC 功能編輯控制項](../../mfc/reference/cmfcribbonedit-class.md)的顯示。

```cpp
virtual void Redraw();
```

### <a name="remarks"></a>備註

此方法通過間接調用`CMFCRibbonEdit`[CWnd::redrawWindow,](/windows/win32/api/winuser/nf-winuser-redrawwindow)並設置了RDW_INVALIDATE、RDW_ERASE和RDW_UPDATENOW標誌,從而重繪對象的顯示矩形。

## <a name="cmfcribboneditsetaccdata"></a><a name="setaccdata"></a>CMFC 功能編輯:設定ACC資料

設置[CMFC 功能編輯](../../mfc/reference/cmfcribbonedit-class.md)物件的輔助功能數據。

```cpp
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>參數

*pParent*<br/>
指向`CMFCRibbonEdit`物件的父視窗。

*資料*<br/>
`CMFCRibbonEdit`對象的輔助功能數據。

### <a name="return-value"></a>傳回值

始終返回 TRUE。

### <a name="remarks"></a>備註

## <a name="cmfcribboneditsetedittext"></a><a name="setedittext"></a>CMFC 功能編輯::設定編輯文字

在文字框中設定文本。

```cpp
void SetEditText(CString strText);
```

### <a name="parameters"></a>參數

*斯特文字*<br/>
[在]文字框的文字。

## <a name="cmfcribboneditsettextalign"></a><a name="settextalign"></a>CMFC 剪彩編輯::設定文字對齊

設定文字框的文字對齊方式。

```cpp
void SetTextAlign(int nAlign);
```

### <a name="parameters"></a>參數

*N 對齊*<br/>
[在]文字對齊枚舉值。 有關可能的值,請參閱備註部分。

### <a name="remarks"></a>備註

參數*nAlign*是以下編輯控制項樣式之一:

- 左對齊ES_LEFT

- 用於中心對齊的ES_CENTER

- 用於正確對齊的ES_RIGHT

有關這些樣式的詳細資訊,請參閱[編輯控制項樣式](/windows/win32/Controls/edit-control-styles)。

## <a name="cmfcribboneditsetwidth"></a><a name="setwidth"></a>CMFC 功能編輯::設定寬度

設置[CMFC 功能編輯](../../mfc/reference/cmfcribbonedit-class.md)控制項的文字框的寬度。

```cpp
void SetWidth(
    int nWidth,
    BOOL bInFloatyMode = FALSE);
```

### <a name="parameters"></a>參數

*n 寬度*<br/>
[在]文字框的寬度(以像素為單位)。

*bInFloatyMode*<br/>
TRUE 設置為浮動模式的寬度;FALSE 設置為常規模式的寬度。

### <a name="remarks"></a>備註

控件`CMFCRibbonEdit`有兩個寬度,具體取決於其顯示模式:浮動模式和常規模式。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton 類別](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[CMFCRibbonBar 類別](../../mfc/reference/cmfcribbonbar-class.md)
