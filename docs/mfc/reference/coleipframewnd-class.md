---
title: Coleipframewnd 來衍生類別
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
ms.openlocfilehash: 483998529b83d9b28c6ab1b219c4f5288dbd8ec7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503824"
---
# <a name="coleipframewnd-class"></a>Coleipframewnd 來衍生類別

應用程式就地編輯視窗的基底。

## <a name="syntax"></a>語法

```
class COleIPFrameWnd : public CFrameWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[Coleipframewnd 來衍生:: Coleipframewnd 來衍生](#coleipframewnd)|建構 `COleIPFrameWnd` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleIPFrameWnd::OnCreateControlBars](#oncreatecontrolbars)|當啟用就地編輯的專案時, 由架構呼叫。|
|[COleIPFrameWnd::RepositionFrame](#repositionframe)|由架構呼叫, 以重新調整就地編輯視窗的位置。|

## <a name="remarks"></a>備註

這個類別會在容器應用程式的文件視窗中建立並放置控制列。 當使用者調整就地編輯視窗的大小時, 它也會處理內嵌[COleResizeBar](../../mfc/reference/coleresizebar-class.md)物件所產生的通知。

如需有關使用`COleIPFrameWnd`的詳細資訊, 請參閱[啟用](../../mfc/activation-cpp.md)文章。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`COleIPFrameWnd`

## <a name="requirements"></a>需求

**標頭:** afxole。h

##  <a name="coleipframewnd"></a>Coleipframewnd 來衍生:: Coleipframewnd 來衍生

會建立`COleIPFrameWnd`物件, 並初始化其就地狀態資訊, 並儲存在 OLEINPLACEFRAMEINFO 類型的結構中。

```
COleIPFrameWnd();
```

### <a name="remarks"></a>備註

如需詳細資訊, 請參閱 Windows SDK 中的[OLEINPLACEFRAMEINFO](/windows/win32/api/oleidl/ns-oleidl-oifi) 。

##  <a name="oncreatecontrolbars"></a>Coleipframewnd 來衍生:: OnCreateControlBars

當啟用就地編輯`OnCreateControlBars`的專案時, 架構會呼叫函數。

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
容器應用程式框架視窗的指標。

*pWndDoc*<br/>
容器檔案層級視窗的指標。 如果容器是 SDI 應用程式, 則可以是 Null。

### <a name="return-value"></a>傳回值

成功時為非零;否則為0。

### <a name="remarks"></a>備註

預設實作不做任何動作。 覆寫此函式, 以執行建立控制列時所需的任何特殊處理。

##  <a name="repositionframe"></a>Coleipframewnd 來衍生:: RepositionFrame

架構會呼叫`RepositionFrame`成員函式來配置控制列, 並重新調整就地編輯視窗的位置, 使其全部可見。

```
virtual void RepositionFrame(
    LPCRECT lpPosRect,
    LPCRECT lpClipRect);
```

### <a name="parameters"></a>參數

*lpPosRect*<br/>
`RECT` 結構`CRect`或物件的指標, 其中包含就地框架視窗的目前位置座標 (以圖元為單位), 相對於工作區。

*lpClipRect*<br/>
`RECT` 結構`CRect`或物件的指標, 其中包含就地框架視窗的目前裁剪矩形座標 (以圖元為單位), 相對於工作區。

### <a name="remarks"></a>備註

[容器] 視窗中控制列的配置與非 OLE 框架視窗所執行的版面配置不同。 非 OLE 框架視窗會從給定的框架視窗大小來計算控制列和其他物件的位置, 如同呼叫[CFrameWnd:: RecalcLayout](../../mfc/reference/cframewnd-class.md#recalclayout)。 [用戶端] 區域是控制列的空間, 以及其他物件被減去之後的保留內容。 另一方面`COleIPFrameWnd` , 視窗會根據指定的工作區定位工具列。 換句話說, `CFrameWnd::RecalcLayout` 「從外部的」運作, 而`COleIPFrameWnd::RepositionFrame` 「從內部」開始運作」。

## <a name="see-also"></a>另請參閱

[MFC 範例 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)
