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
ms.openlocfilehash: 41a958c78719f6aedf1cc02f8e3ff5a2dbbf0e1b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368843"
---
# <a name="cmfcribbonseparator-class"></a>CMFCRibbonSeparator 類別

實現功能區分隔符。

## <a name="syntax"></a>語法

```
class CMFCRibbonSeparator : public CMFCRibbonBaseElement
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|||
|-|-|
|名稱|描述|
|[CMFC 剪子分離器:CMFC 剪綵器](#cmfcribbonseparator)|建構 `CMFCRibbonSeparator` 物件。|

### <a name="public-methods"></a>公用方法

|||
|-|-|
|名稱|描述|
|[CMFC 剪綵器::新增清單框](#addtolistbox)|在 **「自訂」** 對話方塊中向 **「指令」** 清單新增分隔符。 (覆寫[CMFC 功能基礎元素::新增清單框](../../mfc/reference/cmfcribbonbaseelement-class.md#addtolistbox).)|
|`CMFCRibbonSeparator::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|`CMFCRibbonSeparator::GetThisClass`|框架用於獲取指向與此類類型關聯的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|

### <a name="protected-methods"></a>保護方法

|||
|-|-|
|名稱|描述|
|[CMFC 剪綵分離器::從](#copyfrom)|一種複製方法,用於從另一個物件設置分隔符的成員變數。|
|[CMFC 剪彩分離器:取得一般大小](#getregularsize)|返回分隔符的大小。|
|[CMFC 剪子分離器:分離器](#isseparator)|指示這是否是分隔符。|
|[CMFC 剪彩分離器::IsTabStop](#istabstop)|指示這是否是製表符。|
|[CMFC 剪彩分離器::OnDraw](#ondraw)|系統調用以在功能區或快速存取工具列上繪製分隔符。|
|[CMFC 剪綵器:在繪製清單](#ondrawonlist)|系統呼叫以在**命令**清單中繪製分隔符。|

## <a name="remarks"></a>備註

功能區分隔符是一條垂直或水平線,用於邏輯地分隔功能區元素。 可以在功能區控制項、主應用程式功能表、功能區狀態列和快速存取工具列上繪製分隔符。

要在應用程式中使用分隔符,請建構新物件並將其添加到主應用程式功能表中,如下所示:

```
CMFCRibbonMainPanel* pMainPanel = m_wndRibbonBar.AddMainCategory(_T("Main Menu"),
    IDB_FILESMALL,
    IDB_FILELARGE);

...
pMainPanel->Add(new CMFCRibbonSeparator(TRUE));
```

致電[CMFC 功能面板::添加分離器](../../mfc/reference/cmfcribbonpanel-class.md#addseparator)以向功能區面板添加分隔符。 分隔符由`AddSeparator`方法在內部分配和添加。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFC 剪子分離器](../../mfc/reference/cmfcribbonseparator-class.md)

## <a name="requirements"></a>需求

**標頭：** afxbaseribbonelement.h

## <a name="cmfcribbonseparatoraddtolistbox"></a><a name="addtolistbox"></a>CMFC 剪綵器::新增清單框

在 **「自訂」** 對話方塊中向 **「指令」** 清單新增分隔符。

```
virtual int AddToListBox(
    CMFCRibbonCommandsListBox* pWndListBox,
    BOOL bDeep);
```

### <a name="parameters"></a>參數

*pWndListBox*<br/>
[在]指向新增分隔符**的命令**列表的指標。

*bDeep*<br/>
[在]忽視。

### <a name="return-value"></a>傳回值

*pWndListBox*指定的清單框中的字串的從零到的索引。

## <a name="cmfcribbonseparatorcmfcribbonseparator"></a><a name="cmfcribbonseparator"></a>CMFC 剪子分離器:CMFC 剪綵器

建構 `CMFCRibbonSeparator` 物件。

```
CMFCRibbonSeparator(BOOL bIsHoriz = FALSE);
```

### <a name="parameters"></a>參數

*比索裡茲*<br/>
[在]如果為 TRUE,則分隔符是水準的;如果為 TRUE,則分離器為水準分離器。如果 FALSE,則分隔符是垂直的。

### <a name="remarks"></a>備註

水準分隔符用於應用程式功能表。 垂直分隔符用於工具列。

### <a name="example"></a>範例

下面的示例演示如何構造`CMFCRibbonSeparator`類的物件。

[!code-cpp[NVC_MFC_RibbonApp#19](../../mfc/reference/codesnippet/cpp/cmfcribbonseparator-class_1.cpp)]

## <a name="cmfcribbonseparatorcopyfrom"></a><a name="copyfrom"></a>CMFC 剪綵分離器::從

一種複製方法,用於從另一個物件設置分隔符的成員變數。

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>參數

*Src*<br/>
[在]要從中複製的源功能區元素。

## <a name="cmfcribbonseparatorgetregularsize"></a><a name="getregularsize"></a>CMFC 剪彩分離器:取得一般大小

返回分隔符的大小。

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向設備內容的指標。

### <a name="return-value"></a>傳回值

給定設備上下文中分隔符的大小。

## <a name="cmfcribbonseparatorisseparator"></a><a name="isseparator"></a>CMFC 剪子分離器:分離器

指示這是否是分隔符。

```
virtual BOOL IsSeparator() const;
```

### <a name="return-value"></a>傳回值

對於此類來說,始終為 TRUE。

## <a name="cmfcribbonseparatoristabstop"></a><a name="istabstop"></a>CMFC 剪彩分離器::IsTabStop

指示這是否是製表符。

```
virtual BOOL IsTabStop() const;
```

### <a name="return-value"></a>傳回值

始終為此類提供 FALSE。

### <a name="remarks"></a>備註

功能區分隔符不是製表位。

## <a name="cmfcribbonseparatorondraw"></a><a name="ondraw"></a>CMFC 剪彩分離器::OnDraw

系統調用以在功能區或快速存取工具列上繪製分隔符。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向設備上下文的指標。

## <a name="cmfcribbonseparatorondrawonlist"></a><a name="ondrawonlist"></a>CMFC 剪綵器:在繪製清單

系統呼叫以在**命令**清單中繪製分隔符。

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
|*pDC*|[在]指向設備上下文的指標。|
|*斯特文字*|[在]清單中顯示的文字。|
|*n文字位移*|[在]在邊界矩形的文本和左側之間間距。|
|*矩形*|[在]指定邊界矩形。|
|*bIs 選擇*|[在]忽視。|
|*突顯突顯*|[在]忽視。|

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)
