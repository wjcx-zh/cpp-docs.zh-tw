---
title: CSplitterWndEx 類別
ms.date: 11/04/2016
f1_keywords:
- CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx::OnDrawSplitter
helpviewer_keywords:
- CSplitterWndEx [MFC], OnDrawSplitter
ms.assetid: 33e5eef3-05e1-4a07-a968-bf9207ce8598
ms.openlocfilehash: d7952e3082bf68cff7ad9ba218073081ee522320
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363916"
---
# <a name="csplitterwndex-class"></a>CSplitterWndEx 類別

表示自訂分割視窗。

## <a name="syntax"></a>語法

```
class CSplitterWndEx : public CSplitterWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|`CSplitterWndEx::CSplitterWndEx`|預設建構函式。|
|`CSplitterWndEx::~CSplitterWndEx`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSplitterwndEx::在牽引器上](#ondrawsplitter)|由框架調用以繪製拆分視窗。 (覆蓋[CSplitterwnd:onDrawSplitter](csplitterwnd-class.md#ondrawsplitter).)|

## <a name="remarks"></a>備註

重寫方法`OnDrawSplitter`以自定義拆分器視窗的圖形元件的外觀。

該`CSplitterWndEx`類與[OnDrawSplitter 邊界](cmfcvisualmanager-class.md#ondrawsplitterborder)[、OnDrawSplitterBox](cmfcvisualmanager-class.md#ondrawsplitterbox)和[OnFillSplitter 背景](cmfcvisualmanager-class.md#onfillsplitterbackground)方法一起使用,這些方法由可視化管理器實現。 要使視覺化管理程式在應用程式中繪製拆分器視窗,請將`CSplitterWnd`類的聲明替換為`CSplitterWndEx`類。 對於幀視窗應用程式,拆分器視窗類在位於 mainfrm.h 中的 CMainFrame 類中聲明。 例如,請參閱示例目錄中`OutlookDemo`的範例。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](cobject-class.md)

[CCmdTarget](ccmdtarget-class.md)

[CWnd](cwnd-class.md)

[CSplitterWnd](csplitterwnd-class.md)

## <a name="requirements"></a>需求

**標題:** afxsplitterwndex.h

## <a name="csplitterwndexondrawsplitter"></a><a name="ondrawsplitter"></a>CSplitterwndEx::在牽引器上

由框架調用以繪製拆分視窗。

```
virtual void OnDrawSplitter(
   CDC* pDC,
   ESplitType nType,
   const CRect& rect
);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向設備上下文的指標。 如果此參數為 NULL,則框架將重繪活動視窗。

*nType*<br/>
[在]`CSplitterWnd::ESplitType`指定要繪製的拆分視窗元素的枚舉值之一。 有效值為 `splitBox`、`splitBar`、`splitIntersection` 和 `splitBorder`。

*矩形*<br/>
[在]指定用於繪製指定分割視窗元素的尺寸和位置的邊界矩形。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../hierarchy-chart.md)<br/>
[類別](mfc-classes.md)<br/>
[CSplitterWnd 類別](csplitterwnd-class.md)<br/>
[CMFCVisualManager 類別](cmfcvisualmanager-class.md)
