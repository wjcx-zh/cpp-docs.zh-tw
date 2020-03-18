---
title: CMFCRibbonSeparator 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::AddToListBox
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::CopyFrom
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::GetRegularSize
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::IsSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::IsTabStop
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::OnDraw
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::OnDrawOnList
helpviewer_keywords:
- CMFCRibbonSeparator [MFC], CMFCRibbonSeparator
- CMFCRibbonSeparator [MFC], AddToListBox
- CMFCRibbonSeparator [MFC], CopyFrom
- CMFCRibbonSeparator [MFC], GetRegularSize
- CMFCRibbonSeparator [MFC], IsSeparator
- CMFCRibbonSeparator [MFC], IsTabStop
- CMFCRibbonSeparator [MFC], OnDraw
- CMFCRibbonSeparator [MFC], OnDrawOnList
ms.assetid: bedb1a53-cb07-4c3c-be12-698c5409e7cf
ms.openlocfilehash: 65321cb80c80a5f4c6b3cf9c67e85b1bfb6f9d11
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445595"
---
# <a name="cmfcribbonseparator-class"></a>CMFCRibbonSeparator 類別

執行功能區分隔符號。

## <a name="syntax"></a>語法

```
class CMFCRibbonSeparator : public CMFCRibbonBaseElement
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|||
|-|-|
|名稱|描述|
|[CMFCRibbonSeparator::CMFCRibbonSeparator](#cmfcribbonseparator)|建構 `CMFCRibbonSeparator` 物件。|

### <a name="public-methods"></a>公用方法

|||
|-|-|
|名稱|描述|
|[CMFCRibbonSeparator::AddToListBox](#addtolistbox)|在 [**自訂**] 對話方塊的 [**命令**] 清單中加入分隔符號。 （覆寫[CMFCRibbonBaseElement：： AddToListBox](../../mfc/reference/cmfcribbonbaseelement-class.md#addtolistbox)。）|
|`CMFCRibbonSeparator::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|`CMFCRibbonSeparator::GetThisClass`|供架構用來取得與這個類別類型相關聯之[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|

### <a name="protected-methods"></a>受保護的方法

|||
|-|-|
|名稱|描述|
|[CMFCRibbonSeparator：： CopyFrom](#copyfrom)|複製方法，可從另一個物件設定分隔符號的成員變數。|
|[CMFCRibbonSeparator：： GetRegularSize](#getregularsize)|傳回分隔符號的大小。|
|[CMFCRibbonSeparator::IsSeparator](#isseparator)|指出這是否為分隔符號。|
|[CMFCRibbonSeparator：： IsTabStop](#istabstop)|指出這是否為定位停駐點。|
|[CMFCRibbonSeparator：： OnDraw](#ondraw)|由系統呼叫，以在功能區或快速存取工具列上繪製分隔符號。|
|[CMFCRibbonSeparator::OnDrawOnList](#ondrawonlist)|由系統呼叫以在**命令**清單上繪製分隔符號。|

## <a name="remarks"></a>備註

功能區分隔符號是以邏輯方式分隔功能區元素的垂直或水平線條。 分隔符號可以繪製在功能區控制項、主應用程式功能表、功能區狀態列和快速存取工具列上。

若要在您的應用程式中使用分隔符號，請建立新的物件，並將它加入至主應用程式功能表，如下所示：

```
CMFCRibbonMainPanel* pMainPanel = m_wndRibbonBar.AddMainCategory(_T("Main Menu"),
    IDB_FILESMALL,
    IDB_FILELARGE);

...
pMainPanel->Add(new CMFCRibbonSeparator(TRUE));
```

呼叫[CMFCRibbonPanel：： AddSeparator](../../mfc/reference/cmfcribbonpanel-class.md#addseparator)以將分隔符號加入功能區面板。 `AddSeparator` 方法會在內部配置和加入分隔符號。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonSeparator](../../mfc/reference/cmfcribbonseparator-class.md)

## <a name="requirements"></a>需求

**標頭：** afxbaseribbonelement.h

##  <a name="addtolistbox"></a>CMFCRibbonSeparator::AddToListBox

在 [**自訂**] 對話方塊的 [**命令**] 清單中加入分隔符號。

```
virtual int AddToListBox(
    CMFCRibbonCommandsListBox* pWndListBox,
    BOOL bDeep);
```

### <a name="parameters"></a>參數

*pWndListBox*<br/>
在加入分隔符號之**命令**清單的指標。

*bDeep*<br/>
在忽略.

### <a name="return-value"></a>傳回值

*PWndListBox*所指定之清單方塊中字串的以零為起始的索引。

##  <a name="cmfcribbonseparator"></a>CMFCRibbonSeparator::CMFCRibbonSeparator

建構 `CMFCRibbonSeparator` 物件。

```
CMFCRibbonSeparator(BOOL bIsHoriz = FALSE);
```

### <a name="parameters"></a>參數

*bIsHoriz*<br/>
在如果為 TRUE，則表示分隔符號為水準;如果為 FALSE，則分隔符號為垂直。

### <a name="remarks"></a>備註

水準分隔符號會在應用程式功能表中使用。 在工具列中使用垂直分隔符號。

### <a name="example"></a>範例

下列範例示範如何建立 `CMFCRibbonSeparator` 類別的物件。

[!code-cpp[NVC_MFC_RibbonApp#19](../../mfc/reference/codesnippet/cpp/cmfcribbonseparator-class_1.cpp)]

##  <a name="copyfrom"></a>CMFCRibbonSeparator：： CopyFrom

複製方法，可從另一個物件設定分隔符號的成員變數。

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>參數

*原始檔案*<br/>
在要複製的來源功能區元素。

##  <a name="getregularsize"></a>CMFCRibbonSeparator：： GetRegularSize

傳回分隔符號的大小。

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
在裝置內容的指標。

### <a name="return-value"></a>傳回值

指定裝置內容上的分隔符號大小。

##  <a name="isseparator"></a>CMFCRibbonSeparator::IsSeparator

指出這是否為分隔符號。

```
virtual BOOL IsSeparator() const;
```

### <a name="return-value"></a>傳回值

此類別一律為 TRUE。

##  <a name="istabstop"></a>CMFCRibbonSeparator：： IsTabStop

指出這是否為定位停駐點。

```
virtual BOOL IsTabStop() const;
```

### <a name="return-value"></a>傳回值

此類別一律為 FALSE。

### <a name="remarks"></a>備註

功能區分隔符號不是定位停駐點。

##  <a name="ondraw"></a>CMFCRibbonSeparator：： OnDraw

由系統呼叫，以在功能區或快速存取工具列上繪製分隔符號。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
在裝置內容的指標。

##  <a name="ondrawonlist"></a>CMFCRibbonSeparator::OnDrawOnList

由系統呼叫以在**命令**清單上繪製分隔符號。

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

|||
|-|-|
|參數|描述|
|*pDC*|在裝置內容的指標。|
|*strText*|在顯示在清單上的文字。|
|*nTextOffset*|在周框的文字和左邊的間距。|
|*各種*|在指定周框。|
|*bIsSelected*|在忽略.|
|*bHighlighted*|在忽略.|

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)
