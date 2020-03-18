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
ms.openlocfilehash: a8048f860a2cce75c37a065cfdd2751141054f1b
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446239"
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
|[CMFCRibbonCheckBox：： GetCompactSize](#getcompactsize)|（覆寫[CMFCRibbonButton：： GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize)。）|
|[CMFCRibbonCheckBox：： GetIntermediateSize](#getintermediatesize)|（覆寫[CMFCRibbonButton：： GetIntermediateSize](../../mfc/reference/cmfcribbonbutton-class.md#getintermediatesize)。）|
|[CMFCRibbonCheckBox：： GetRegularSize](#getregularsize)|（覆寫[CMFCRibbonButton：： GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize)。）|
|[CMFCRibbonCheckBox::IsDrawTooltipImage](#isdrawtooltipimage)|(覆寫 `CMFCRibbonButton::IsDrawTooltipImage`)。|
|[CMFCRibbonCheckBox：： OnDraw](#ondraw)|（覆寫[CMFCRibbonButton：： OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw)。）|
|[CMFCRibbonCheckBox：： OnDrawMenuImage](#ondrawmenuimage)|（覆寫[CMFCRibbonBaseElement：： OnDrawMenuImage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage)。）|
|[CMFCRibbonCheckBox::OnDrawOnList](#ondrawonlist)|(覆寫 `CMFCRibbonButton::OnDrawOnList`)。|
|[CMFCRibbonCheckBox：： SetACCData](#setaccdata)|（覆寫[CMFCRibbonButton：： SetACCData](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata)。）|

## <a name="remarks"></a>備註

若要在應用程式中使用 `CMFCRibbonCheckBox`，請將下列建構函式加入至您的程式碼：

```
CMFCRibbonCheckBox (UINT nID, LPCTSTR lpszText)
```

其中， *nID*是核取方塊命令 ID，而*lpszText*是核取方塊的文字標籤。

您可以使用[CMFCRibbonPanel：： add](../../mfc/reference/cmfcribbonpanel-class.md#add)，將核取方塊新增至功能區面板。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonCheckBox](../../mfc/reference/cmfcribboncheckbox-class.md)

## <a name="requirements"></a>需求

**標頭：** afxribboncheckbox。h

##  <a name="cmfcribboncheckbox"></a>CMFCRibbonCheckBox::CMFCRibbonCheckBox

功能區核取方塊物件的構造函式

```
CMFCRibbonCheckBox(
    UINT nID,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>參數

*nID*<br/>
在指定命令識別碼。

*lpszText*<br/>
在指定文字標籤。

### <a name="return-value"></a>傳回值

建立功能區核取方塊物件。

### <a name="example"></a>範例

下列範例示範如何建立 `CMFCRibbonCheckBox` 類別的物件。

[!code-cpp[NVC_MFC_RibbonApp#17](../../mfc/reference/codesnippet/cpp/cmfcribboncheckbox-class_1.cpp)]

##  <a name="getcompactsize"></a>CMFCRibbonCheckBox：： GetCompactSize

當覆寫時，取得核取方塊的壓縮大小。

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
在與核取方塊相關聯之 CDC 的指標。

### <a name="return-value"></a>傳回值

傳回 `CSize` 物件，其中包含核取方塊的壓縮大小。

### <a name="remarks"></a>備註

如果未覆寫，則會傳回復選框的中繼大小。

##  <a name="getintermediatesize"></a>CMFCRibbonCheckBox：： GetIntermediateSize

取得核取方塊的中繼大小。

```
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
在與這個核取方塊相關聯之 CDC 的指標。

### <a name="return-value"></a>傳回值

包含核取方塊之中繼大小的 `CSize` 物件。

### <a name="remarks"></a>備註

如果未覆寫，會將中繼大小計算為預設核取方塊大小（`AFX_CHECK_BOX_DEFAULT_SIZE`）加上文字大小，再加上邊界。

##  <a name="getregularsize"></a>CMFCRibbonCheckBox：： GetRegularSize

取得核取方塊的一般大小。

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
在與這個核取方塊相關聯之 CDC 物件的指標。

### <a name="return-value"></a>傳回值

傳回包含核取方塊一般大小的 `CSize` 物件。

### <a name="remarks"></a>備註

如果未覆寫，則會傳回復選框的中繼大小。

##  <a name="isdrawtooltipimage"></a>CMFCRibbonCheckBox::IsDrawTooltipImage

指出是否有與核取方塊相關聯的工具提示影像。

```
virtual BOOL IsDrawTooltipImage() const;
```

### <a name="return-value"></a>傳回值

如果有與核取方塊相關聯的工具提示影像，則傳回 TRUE，否則傳回 FALSE。

### <a name="remarks"></a>備註

##  <a name="ondraw"></a>CMFCRibbonCheckBox：： OnDraw

由架構呼叫，以使用指定的裝置內容繪製核取方塊。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
在要在其中繪製核取方塊之 CDC 的指標。

### <a name="remarks"></a>備註

##  <a name="ondrawmenuimage"></a>CMFCRibbonCheckBox：： OnDrawMenuImage

由架構呼叫以繪製核取方塊的功能表影像。

```
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```

### <a name="parameters"></a>參數

在*CDC&#42;*<br/>
與核取方塊相關聯之 CDC 的指標。

*CRect*<br/>
在`CRect` 物件，指定要在其中繪製功能表影像的矩形。

### <a name="return-value"></a>傳回值

如果已繪製影像，則傳回 TRUE，否則傳回 FALSE。

### <a name="remarks"></a>備註

如果未覆寫，則會傳回 FALSE。

##  <a name="ondrawonlist"></a>CMFCRibbonCheckBox::OnDrawOnList

由架構呼叫，以在 [命令] 清單方塊中繪製核取方塊。

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
在要在其中繪製核取方塊之裝置內容的指標。

*strText*<br/>
在顯示文字。

*nTextOffset*<br/>
在從清單方塊左邊到顯示文字的距離（以圖元為單位）。

*各種*<br/>
在核取方塊的顯示矩形。

*bIsSelected*<br/>
在如果已選取核取方塊，則為 TRUE，否則為 FALSE。

*bHighlighted*<br/>
在如果核取方塊反白顯示，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="setaccdata"></a>CMFCRibbonCheckBox：： SetACCData

設定核取方塊的協助工具資料。

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>參數

*pParent*<br/>
核取方塊的父視窗。

*data*<br/>
核取方塊的協助工具資料。

### <a name="return-value"></a>傳回值

一律傳回 TRUE。

### <a name="remarks"></a>備註

根據預設，這個方法會設定核取方塊的協助工具資料，而且一律會傳回 TRUE。 覆寫此方法以設定協助工具資料並傳回值，以指出成功或失敗。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonPanel 類別](../../mfc/reference/cmfcribbonpanel-class.md)
