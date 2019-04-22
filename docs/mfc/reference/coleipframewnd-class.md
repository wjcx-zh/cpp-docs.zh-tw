---
title: COleIPFrameWnd 類別
ms.date: 11/04/2016
f1_keywords:
- COleIPFrameWnd
- AFXOLE/COleIPFrameWnd
- AFXOLE/COleIPFrameWnd::COleIPFrameWnd
- AFXOLE/COleIPFrameWnd::OnCreateControlBars
- AFXOLE/COleIPFrameWnd::RepositionFrame
helpviewer_keywords:
- COleIPFrameWnd [MFC], COleIPFrameWnd
- COleIPFrameWnd [MFC], OnCreateControlBars
- COleIPFrameWnd [MFC], RepositionFrame
ms.assetid: 24abb2cb-826c-4dda-a287-d8a8900a5763
ms.openlocfilehash: 34388e635ba89d732ae3993074a2c8268e2289a3
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58779608"
---
# <a name="coleipframewnd-class"></a>COleIPFrameWnd 類別

應用程式就地編輯視窗的基底。

## <a name="syntax"></a>語法

```
class COleIPFrameWnd : public CFrameWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COleIPFrameWnd::COleIPFrameWnd](#coleipframewnd)|建構 `COleIPFrameWnd` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleIPFrameWnd::OnCreateControlBars](#oncreatecontrolbars)|當項目啟動就地編輯時由架構呼叫。|
|[COleIPFrameWnd::RepositionFrame](#repositionframe)|由架構呼叫以調整就地編輯視窗的位置。|

## <a name="remarks"></a>備註

這個類別會建立與位置控制容器應用程式的文件視窗內的橫條圖。 它也會處理通知的產生的內嵌[COleResizeBar](../../mfc/reference/coleresizebar-class.md)當使用者調整就地編輯視窗的物件。

如需有關使用`COleIPFrameWnd`，請參閱文章[啟用](../../mfc/activation-cpp.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`COleIPFrameWnd`

## <a name="requirements"></a>需求

**標頭：** afxole.h

##  <a name="coleipframewnd"></a>  COleIPFrameWnd::COleIPFrameWnd

建構`COleIPFrameWnd`物件，並初始化其就地狀態資訊，它會儲存在類型 OLEINPLACEFRAMEINFO 的結構。

```
COleIPFrameWnd();
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [OLEINPLACEFRAMEINFO](/windows/desktop/api/oleidl/ns-oleidl-tagoifi) Windows SDK 中。

##  <a name="oncreatecontrolbars"></a>  COleIPFrameWnd::OnCreateControlBars

這個架構會呼叫`OnCreateControlBars`函式時項目啟動就地編輯。

```
virtual BOOL OnCreateControlBars(
    CWnd* pWndFrame,
    CWnd* pWndDoc);

virtual BOOL OnCreateControlBars(
    CFrameWnd* pWndFrame,
    CFrameWnd* pWndDoc);
```

### <a name="parameters"></a>參數

*pWndFrame*<br/>
容器應用程式的框架視窗的指標。

*pWndDoc*<br/>
在容器文件層級視窗的指標。 如果容器為 SDI 應用程式時，就可以是 NULL。

### <a name="return-value"></a>傳回值

非零成功;否則就是 0。

### <a name="remarks"></a>備註

預設實作不做任何動作。 覆寫這個函式來執行時所建立的控制列所需的任何特殊處理。

##  <a name="repositionframe"></a>  COleIPFrameWnd::RepositionFrame

這個架構會呼叫`RepositionFrame`控制列版面配置和調整就地編輯視窗的位置，因此全部都是可見的成員函式。

```
virtual void RepositionFrame(
    LPCRECT lpPosRect,
    LPCRECT lpClipRect);
```

### <a name="parameters"></a>參數

*lpPosRect*<br/>
指標`RECT`結構或`CRect`物件，其中包含該就地框架視窗的目前位置座標，以像素為單位，相對於用戶端區域中。

*lpClipRect*<br/>
指標`RECT`結構或`CRect`物件，其中包含該就地框架視窗的目前裁剪矩形的座標，像素為單位，相對於用戶端區域。

### <a name="remarks"></a>備註

在 [容器] 視窗的控制列的配置與 1-up，由非 OLE 框架視窗來執行。 在非 OLE 框架視窗會計算控制列和指定的框架視窗大小，如所示的呼叫的其他物件的位置[CFrameWnd::RecalcLayout](../../mfc/reference/cframewnd-class.md#recalclayout)。 工作區是剩下之後減去控制列和其他物件的空間。 A `COleIPFrameWnd`  視窗中，相反地，將工具列，根據給定的用戶端區域。 亦即`CFrameWnd::RecalcLayout`運作 」 從，在外部"，而`COleIPFrameWnd::RepositionFrame`"由內而外。 」 的運作方式

## <a name="see-also"></a>另請參閱

[MFC 範例 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)
