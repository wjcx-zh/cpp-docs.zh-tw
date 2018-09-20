---
title: CMFCRibbonSeparator 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fb8c01145a3f4f0019ca27f38bccb63aa8ab6227
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375355"
---
# <a name="cmfcribbonseparator-class"></a>CMFCRibbonSeparator 類別

實作功能區分隔符號。

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
|[CMFCRibbonSeparator::AddToListBox](#addtolistbox)|加入分隔符號**命令**列入**自訂** 對話方塊。 (覆寫[CMFCRibbonBaseElement::AddToListBox](../../mfc/reference/cmfcribbonbaseelement-class.md#addtolistbox)。)|
|`CMFCRibbonSeparator::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|`CMFCRibbonSeparator::GetThisClass`|Framework 用來取得的指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|

### <a name="protected-methods"></a>保護方法

|||
|-|-|
|名稱|描述|
|[CMFCRibbonSeparator::CopyFrom](#copyfrom)|複製方法，以從另一個物件設定為分隔符號的成員變數。|
|[CMFCRibbonSeparator::GetRegularSize](#getregularsize)|傳回分隔符號的大小。|
|[CMFCRibbonSeparator::IsSeparator](#isseparator)|指出這是否為分隔符號。|
|[CMFCRibbonSeparator::IsTabStop](#istabstop)|指出這是否為定位停駐點。|
|[CMFCRibbonSeparator::OnDraw](#ondraw)|若要快速存取工具列或功能區上繪製分隔符號系統呼叫。|
|[CMFCRibbonSeparator::OnDrawOnList](#ondrawonlist)|呼叫系統上繪製分隔符號**命令**清單。|

## <a name="remarks"></a>備註

功能區分隔符號是垂直或水平的一行，以邏輯方式分隔功能區項目。 在功能區控制項、 主應用程式 功能表、 功能區狀態列，以及快速存取工具列上，可以繪製分隔符號。

若要使用分隔符號，在您的應用程式中，建構新的物件，並將它新增至主應用程式功能表，如下所示：

```
CMFCRibbonMainPanel* pMainPanel = m_wndRibbonBar.AddMainCategory(_T("Main Menu"),
    IDB_FILESMALL,
    IDB_FILELARGE);

...
pMainPanel->Add(new CMFCRibbonSeparator(TRUE));
```
呼叫[CMFCRibbonPanel::AddSeparator](../../mfc/reference/cmfcribbonpanel-class.md#addseparator)加入功能區面板中的分隔符號。 分隔符號會配置並在內部新增`AddSeparator`方法。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonSeparator](../../mfc/reference/cmfcribbonseparator-class.md)

## <a name="requirements"></a>需求

**標頭：** afxbaseribbonelement.h

##  <a name="addtolistbox"></a>  CMFCRibbonSeparator::AddToListBox

加入分隔符號**命令**列入**自訂** 對話方塊。

```
virtual int AddToListBox(
    CMFCRibbonCommandsListBox* pWndListBox,
    BOOL bDeep);
```

### <a name="parameters"></a>參數

*pWndListBox*<br/>
[in]指標**命令**加入分隔符號的位置清單。

*bDeep*<br/>
[in]略過。

### <a name="return-value"></a>傳回值

在清單方塊中所指定的字串以零起始的索引*pWndListBox*。

##  <a name="cmfcribbonseparator"></a>  CMFCRibbonSeparator::CMFCRibbonSeparator

建構 `CMFCRibbonSeparator` 物件。

```
CMFCRibbonSeparator(BOOL bIsHoriz = FALSE);
```

### <a name="parameters"></a>參數

*bIsHoriz*<br/>
[in]如果為 TRUE，分隔符號是水平;如果為 FALSE，分隔符號是垂直。

### <a name="remarks"></a>備註

應用程式功能表中，會使用水平分隔符號。 工具列中，會使用垂直分隔符號。

### <a name="example"></a>範例

下列範例示範如何建構的物件`CMFCRibbonSeparator`類別。

[!code-cpp[NVC_MFC_RibbonApp#19](../../mfc/reference/codesnippet/cpp/cmfcribbonseparator-class_1.cpp)]

##  <a name="copyfrom"></a>  CMFCRibbonSeparator::CopyFrom

複製方法，以從另一個物件設定為分隔符號的成員變數。

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>參數

*src*<br/>
[in]要複製的來源功能區項目。

##  <a name="getregularsize"></a>  CMFCRibbonSeparator::GetRegularSize

傳回分隔符號的大小。

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[in]裝置內容指標。

### <a name="return-value"></a>傳回值

指定的裝置內容的分隔符號的大小。

##  <a name="isseparator"></a>  CMFCRibbonSeparator::IsSeparator

指出這是否為分隔符號。

```
virtual BOOL IsSeparator() const;
```

### <a name="return-value"></a>傳回值

一律適用於這個類別。

##  <a name="istabstop"></a>  CMFCRibbonSeparator::IsTabStop

指出這是否為定位停駐點。

```
virtual BOOL IsTabStop() const;
```

### <a name="return-value"></a>傳回值

永遠為 FALSE 的這個類別。

### <a name="remarks"></a>備註

功能區分隔符號不是定位停駐點。

##  <a name="ondraw"></a>  CMFCRibbonSeparator::OnDraw

若要快速存取工具列或功能區上繪製分隔符號系統呼叫。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[in]裝置內容指標。

##  <a name="ondrawonlist"></a>  CMFCRibbonSeparator::OnDrawOnList

呼叫系統上繪製分隔符號**命令**清單。

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
|*pDC*|[in]裝置內容指標。|
|*先把 strText*|[in]在清單上顯示的文字。|
|*nTextOffset*|[in]與文字之間的週框矩形左邊的間距。|
|*rect*|[in]指定週框矩形。|
|*bIsSelected*|[in]略過。|
|*bHighlighted*|[in]略過。|

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)
