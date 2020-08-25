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
ms.openlocfilehash: f435dc5ae8821a6d5626af2f93710a1672fd374c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831797"
---
# <a name="cmfcribbonseparator-class"></a>CMFCRibbonSeparator 類別

實行功能區分隔符號。

## <a name="syntax"></a>語法

```
class CMFCRibbonSeparator : public CMFCRibbonBaseElement
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|-|-|
|[CMFCRibbonSeparator::CMFCRibbonSeparator](#cmfcribbonseparator)|建構 `CMFCRibbonSeparator` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|-|-|
|[CMFCRibbonSeparator::AddToListBox](#addtolistbox)|在 [**自訂**] 對話方塊的 [**命令**] 清單中加入分隔符號。  (覆寫 [CMFCRibbonBaseElement：： AddToListBox](../../mfc/reference/cmfcribbonbaseelement-class.md#addtolistbox)。 ) |
|`CMFCRibbonSeparator::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|`CMFCRibbonSeparator::GetThisClass`|由架構用來取得與這個類別類型相關聯之 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 物件的指標。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|-|-|
|[CMFCRibbonSeparator：： CopyFrom](#copyfrom)|從另一個物件設定分隔符號之成員變數的複製方法。|
|[CMFCRibbonSeparator：： GetRegularSize](#getregularsize)|傳回分隔符號的大小。|
|[CMFCRibbonSeparator::IsSeparator](#isseparator)|指出這是否為分隔符號。|
|[CMFCRibbonSeparator：： IsTabStop](#istabstop)|指出這是否為 tab 鍵停用。|
|[CMFCRibbonSeparator：： OnDraw](#ondraw)|由系統呼叫，以在功能區或快速存取工具列上繪製分隔符號。|
|[CMFCRibbonSeparator::OnDrawOnList](#ondrawonlist)|由系統呼叫以在 **命令** 清單上繪製分隔符號。|

## <a name="remarks"></a>備註

功能區分隔符號是以邏輯方式分隔功能區專案的垂直或水平線條。 您可以在功能區控制項、主要應用程式功能表、功能區狀態列和快速存取工具列上繪製分隔符號。

若要在您的應用程式中使用分隔符號，請建立新的物件，並將它新增至主應用程式功能表，如下所示：

```
CMFCRibbonMainPanel* pMainPanel = m_wndRibbonBar.AddMainCategory(_T("Main Menu"),
    IDB_FILESMALL,
    IDB_FILELARGE);

...
pMainPanel->Add(new CMFCRibbonSeparator(TRUE));
```

呼叫 [CMFCRibbonPanel：： AddSeparator](../../mfc/reference/cmfcribbonpanel-class.md#addseparator) ，將分隔符號加入功能區面板。 分隔符號會由方法在內部配置和新增 `AddSeparator` 。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonSeparator](../../mfc/reference/cmfcribbonseparator-class.md)

## <a name="requirements"></a>規格需求

**標頭：** afxbaseribbonelement.h

## <a name="cmfcribbonseparatoraddtolistbox"></a><a name="addtolistbox"></a> CMFCRibbonSeparator::AddToListBox

在 [**自訂**] 對話方塊的 [**命令**] 清單中加入分隔符號。

```
virtual int AddToListBox(
    CMFCRibbonCommandsListBox* pWndListBox,
    BOOL bDeep);
```

### <a name="parameters"></a>參數

*pWndListBox*<br/>
在加入分隔符號之 **命令** 清單的指標。

*bDeep*<br/>
在忽視。

### <a name="return-value"></a>傳回值

以零為基底的索引，指向 *pWndListBox*所指定清單方塊中的字串。

## <a name="cmfcribbonseparatorcmfcribbonseparator"></a><a name="cmfcribbonseparator"></a> CMFCRibbonSeparator::CMFCRibbonSeparator

建構 `CMFCRibbonSeparator` 物件。

```
CMFCRibbonSeparator(BOOL bIsHoriz = FALSE);
```

### <a name="parameters"></a>參數

*bIsHoriz*<br/>
在若為 TRUE，則為水準分隔符號;如果為 FALSE，則表示分隔符號為垂直。

### <a name="remarks"></a>備註

在應用程式功能表中使用水準分隔符號。 在工具列中使用垂直分隔符號。

### <a name="example"></a>範例

下列範例示範如何建立類別的物件 `CMFCRibbonSeparator` 。

[!code-cpp[NVC_MFC_RibbonApp#19](../../mfc/reference/codesnippet/cpp/cmfcribbonseparator-class_1.cpp)]

## <a name="cmfcribbonseparatorcopyfrom"></a><a name="copyfrom"></a> CMFCRibbonSeparator：： CopyFrom

從另一個物件設定分隔符號之成員變數的複製方法。

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>參數

*Src*<br/>
在要複製的來源功能區元素。

## <a name="cmfcribbonseparatorgetregularsize"></a><a name="getregularsize"></a> CMFCRibbonSeparator：： GetRegularSize

傳回分隔符號的大小。

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>參數

*Pdc*<br/>
在裝置內容的指標。

### <a name="return-value"></a>傳回值

給定裝置內容上分隔符號的大小。

## <a name="cmfcribbonseparatorisseparator"></a><a name="isseparator"></a> CMFCRibbonSeparator::IsSeparator

指出這是否為分隔符號。

```
virtual BOOL IsSeparator() const;
```

### <a name="return-value"></a>傳回值

此類別一律為 TRUE。

## <a name="cmfcribbonseparatoristabstop"></a><a name="istabstop"></a> CMFCRibbonSeparator：： IsTabStop

指出這是否為 tab 鍵停用。

```
virtual BOOL IsTabStop() const;
```

### <a name="return-value"></a>傳回值

此類別一律為 FALSE。

### <a name="remarks"></a>備註

功能區分隔符號不是定位停駐點。

## <a name="cmfcribbonseparatorondraw"></a><a name="ondraw"></a> CMFCRibbonSeparator：： OnDraw

由系統呼叫，以在功能區或快速存取工具列上繪製分隔符號。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>參數

*Pdc*<br/>
在裝置內容的指標。

## <a name="cmfcribbonseparatorondrawonlist"></a><a name="ondrawonlist"></a> CMFCRibbonSeparator::OnDrawOnList

由系統呼叫以在 **命令** 清單上繪製分隔符號。

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

*Pdc*\
在裝置內容的指標。

*strText*\
在顯示在清單上的文字。

*nTextOffset*\
在文字和周框左邊的間距。

*矩形*\
在指定周框。

*bIsSelected*\
在忽視。

*bHighlighted*\
在忽視。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)
