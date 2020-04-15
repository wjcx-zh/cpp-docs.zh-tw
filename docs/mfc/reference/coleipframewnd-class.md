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
ms.openlocfilehash: 01e259cf01c42add26088b0cbd2f6dab311eb9b1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374962"
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
|[COleIPFramewnd:COleIPFramewnd](#coleipframewnd)|建構 `COleIPFrameWnd` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleIPFramewnd::在建立控制列上](#oncreatecontrolbars)|當專案被啟動進行就地編輯時,由框架調用。|
|[COleIPFramewnd::重新置放框架](#repositionframe)|由框架調用重新置放就地編輯視窗。|

## <a name="remarks"></a>備註

此類在容器應用程式的文件視窗中創建和定位控制欄。 當使用者調整就地編輯視窗的大小時,它還處理由嵌入式[COle ResizeBar](../../mfc/reference/coleresizebar-class.md)物件生成的通知。

有關使用`COleIPFrameWnd`的詳細資訊,請參閱文章[啟動](../../mfc/activation-cpp.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`COleIPFrameWnd`

## <a name="requirements"></a>需求

**標題:** afxole.h

## <a name="coleipframewndcoleipframewnd"></a><a name="coleipframewnd"></a>COleIPFramewnd:COleIPFramewnd

構造`COleIPFrameWnd`物件並初始化其就地狀態資訊,這些資訊存儲在 OLEINPLACEFRAMEINFO 類型的結構中。

```
COleIPFrameWnd();
```

### <a name="remarks"></a>備註

有關詳細資訊,請參閱 Windows SDK 中的[OLEINPLACEFRAMEINFO。](/windows/win32/api/oleidl/ns-oleidl-oleinplaceframeinfo)

## <a name="coleipframewndoncreatecontrolbars"></a><a name="oncreatecontrolbars"></a>COleIPFramewnd::在建立控制列上

當啟動項目進行`OnCreateControlBars`就地編輯時,框架將調用該函數。

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
指向容器應用程式的幀視窗的指標。

*普恩德多克*<br/>
指向容器的文件級視窗的指標。 如果容器是 SDI 應用程式,則可以為 NULL。

### <a name="return-value"></a>傳回值

成功時為非零;否則,0。

### <a name="remarks"></a>備註

預設實作不做任何動作。 重寫此函數以在創建控制條時執行所需的任何特殊處理。

## <a name="coleipframewndrepositionframe"></a><a name="repositionframe"></a>COleIPFramewnd::重新置放框架

框架調用`RepositionFrame`成員函數來佈局控制欄並重新置放就地編輯視窗,以便所有控制項都可見。

```
virtual void RepositionFrame(
    LPCRECT lpPosRect,
    LPCRECT lpClipRect);
```

### <a name="parameters"></a>參數

*lpPosRect*<br/>
指向`RECT`包含就地幀`CRect`視窗 當前位置座標的結構或物件(以像素為單位)相對於工作區的指標。

*lpClipRect*<br/>
指向`RECT`包含就地框架`CRect`視窗 當前剪切矩形座標的結構或物件(以圖元為單位)相對於工作區的指標。

### <a name="remarks"></a>備註

容器視窗中的控制欄的佈局不同於非 OLE 框架視窗執行的佈局。 非 OLE 框架視窗計算來自給定畫面視窗大小的控制條和其他物件的位置,如對[CFrameWnd 的呼叫::recalcLayout](../../mfc/reference/cframewnd-class.md#recalclayout)。 工作區是減去控制條和其他對象的空間後保留的內容。 另`COleIPFrameWnd`一方面,窗口根據給定的工作區定位工具列。 換句話說,`CFrameWnd::RecalcLayout`作品"從外面",`COleIPFrameWnd::RepositionFrame`而 工作"從內到外"。

## <a name="see-also"></a>另請參閱

[MFC 樣品 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)
