---
title: CMFCRibbonCheckBox 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetCompactSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetIntermediateSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetRegularSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::IsDrawTooltipImage
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDraw
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDrawMenuImage
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDrawOnList
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::SetACCData
helpviewer_keywords:
- CMFCRibbonCheckBox [MFC], CMFCRibbonCheckBox
- CMFCRibbonCheckBox [MFC], GetCompactSize
- CMFCRibbonCheckBox [MFC], GetIntermediateSize
- CMFCRibbonCheckBox [MFC], GetRegularSize
- CMFCRibbonCheckBox [MFC], IsDrawTooltipImage
- CMFCRibbonCheckBox [MFC], OnDraw
- CMFCRibbonCheckBox [MFC], OnDrawMenuImage
- CMFCRibbonCheckBox [MFC], OnDrawOnList
- CMFCRibbonCheckBox [MFC], SetACCData
ms.assetid: 3a6c3891-c8d1-4af0-b954-7b9ab048782a
ms.openlocfilehash: 067f38522c1be112d6e12200c2c10e1d439e5057
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612416"
---
# <a name="cmfcribboncheckbox-class"></a>CMFCRibbonCheckBox 類別

`CMFCRibbonCheckBox` 類別實作可以加入至功能區面板、快速存取工具列或快顯功能表的核取方塊。

## <a name="syntax"></a>語法

```
class CMFCRibbonCheckBox : public CMFCRibbonButton
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCRibbonCheckBox::CMFCRibbonCheckBox](#cmfcribboncheckbox)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCRibbonCheckBox::GetCompactSize](#getcompactsize)|(覆寫[cmfcribbonbutton:: Getcompactsize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize)。)|
|[CMFCRibbonCheckBox::GetIntermediateSize](#getintermediatesize)|(覆寫[cmfcribbonbutton:: Getintermediatesize](../../mfc/reference/cmfcribbonbutton-class.md#getintermediatesize)。)|
|[CMFCRibbonCheckBox::GetRegularSize](#getregularsize)|(覆寫[cmfcribbonbutton:: Getregularsize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize)。)|
|[CMFCRibbonCheckBox::IsDrawTooltipImage](#isdrawtooltipimage)|(覆寫 `CMFCRibbonButton::IsDrawTooltipImage`。)|
|[CMFCRibbonCheckBox::OnDraw](#ondraw)|(覆寫[cmfcribbonbutton:: Ondraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw)。)|
|[CMFCRibbonCheckBox::OnDrawMenuImage](#ondrawmenuimage)|(覆寫[cmfcribbonbaseelement:: Ondrawmenuimage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage)。)|
|[CMFCRibbonCheckBox::OnDrawOnList](#ondrawonlist)|(覆寫 `CMFCRibbonButton::OnDrawOnList`。)|
|[CMFCRibbonCheckBox::SetACCData](#setaccdata)|(覆寫[cmfcribbonbutton:: Setaccdata](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata)。)|

## <a name="remarks"></a>備註

若要在應用程式中使用 `CMFCRibbonCheckBox`，請將下列建構函式加入至您的程式碼：

```
CMFCRibbonCheckBox (UINT nID, LPCTSTR lpszText)
```
其中*nID*  核取方塊的命令識別碼並*lpszText*文字標籤，核取方塊。

您也可以使用功能區面板新增核取方塊[cmfcribbonpanel:: Add](../../mfc/reference/cmfcribbonpanel-class.md#add)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonCheckBox](../../mfc/reference/cmfcribboncheckbox-class.md)

## <a name="requirements"></a>需求

**標頭：** afxribboncheckbox.h

##  <a name="cmfcribboncheckbox"></a>  CMFCRibbonCheckBox::CMFCRibbonCheckBox

功能區核取方塊物件的建構函式

```
CMFCRibbonCheckBox(
    UINT nID,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>參數

*nID*<br/>
[in]指定命令識別碼。

*lpszText*<br/>
[in]指定文字標籤。

### <a name="return-value"></a>傳回值

建構功能區核取方塊物件。

### <a name="example"></a>範例

下列範例示範如何建構的物件`CMFCRibbonCheckBox`類別。

[!code-cpp[NVC_MFC_RibbonApp#17](../../mfc/reference/codesnippet/cpp/cmfcribboncheckbox-class_1.cpp)]

##  <a name="getcompactsize"></a>  CMFCRibbonCheckBox::GetCompactSize

覆寫時，取得核取方塊的壓縮大小。

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[in]核取方塊相關聯的 CDC 的指標。

### <a name="return-value"></a>傳回值

傳回`CSize`物件，其中包含核取方塊的壓縮大小。

### <a name="remarks"></a>備註

如果未覆寫，會傳回中繼核取方塊的大小。

##  <a name="getintermediatesize"></a>  CMFCRibbonCheckBox::GetIntermediateSize

取得中繼核取方塊的大小。

```
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[in]指標，此核取方塊相關聯的 CDC。

### <a name="return-value"></a>傳回值

A`CSize`物件，包含中繼核取方塊的大小。

### <a name="remarks"></a>備註

如果未覆寫，會計算為預設核取方塊大小中繼的大小 ( `AFX_CHECK_BOX_DEFAULT_SIZE`) 再加上文字的大小，再加上邊界。

##  <a name="getregularsize"></a>  CMFCRibbonCheckBox::GetRegularSize

取得規則的核取方塊大小。

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[in]此核取方塊相關聯的 CDC 物件的指標。

### <a name="return-value"></a>傳回值

傳回`CSize`物件，其中包含規則的核取方塊大小。

### <a name="remarks"></a>備註

如果未覆寫，會傳回中繼核取方塊的大小。

##  <a name="isdrawtooltipimage"></a>  CMFCRibbonCheckBox::IsDrawTooltipImage

指出是否核取方塊相關聯的工具提示映像。

```
virtual BOOL IsDrawTooltipImage() const;
```

### <a name="return-value"></a>傳回值

如果有工具提示的映像相關聯的核取方塊，或如果沒有，則為 FALSE，則傳回 TRUE。

### <a name="remarks"></a>備註

##  <a name="ondraw"></a>  CMFCRibbonCheckBox::OnDraw

由架構呼叫以繪製使用指定的裝置內容的核取方塊。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[in]若要在其中繪製核取方塊 CDC 的指標。

### <a name="remarks"></a>備註

##  <a name="ondrawmenuimage"></a>  CMFCRibbonCheckBox::OnDrawMenuImage

由架構呼叫以繪製功能表圖像的核取方塊。

```
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```

### <a name="parameters"></a>參數

[in]*CDC&#42;*<br/>
核取方塊相關聯的 CDC 的指標。

*CRect*<br/>
[in]A`CRect`物件，指定要繪製的功能表影像的矩形。

### <a name="return-value"></a>傳回值

傳回已繪製的影像，如果為 TRUE 或 FALSE，如果不是。

### <a name="remarks"></a>備註

如果未覆寫，會傳回 FALSE。

##  <a name="ondrawonlist"></a>  CMFCRibbonCheckBox::OnDrawOnList

由架構呼叫以繪製命令的清單方塊中的核取方塊。

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
[in]在其中繪製核取方塊的裝置內容指標。

*先把 strText*<br/>
[in]顯示文字。

*nTextOffset*<br/>
[in]距離，以像素為單位，從左側的清單方塊的顯示文字。

*rect*<br/>
[in]核取方塊顯示矩形。

*bIsSelected*<br/>
[in]如果核取方塊為選取狀態，或如果沒有，則為 FALSE，則為 TRUE。

*bHighlighted*<br/>
[in]如果核取方塊反白顯示，或如果沒有，則為 FALSE，則為 TRUE。

### <a name="remarks"></a>備註

##  <a name="setaccdata"></a>  CMFCRibbonCheckBox::SetACCData

設定協助工具資料的核取方塊。

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>參數

*pParent*<br/>
核取方塊的父視窗。

*data*<br/>
協助工具資料的核取方塊。

### <a name="return-value"></a>傳回值

一律會傳回 TRUE。

### <a name="remarks"></a>備註

依預設這個方法會設定協助工具資料的核取方塊，並一律會傳回 TRUE。 覆寫此方法以設定協助工具資料並傳回值，以指出成功或失敗。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonPanel 類別](../../mfc/reference/cmfcribbonpanel-class.md)
