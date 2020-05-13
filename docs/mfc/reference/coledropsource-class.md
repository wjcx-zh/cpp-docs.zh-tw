---
title: COleDropSource 類別
ms.date: 11/04/2016
f1_keywords:
- COleDropSource
- AFXOLE/COleDropSource
- AFXOLE/COleDropSource::COleDropSource
- AFXOLE/COleDropSource::GiveFeedback
- AFXOLE/COleDropSource::OnBeginDrag
- AFXOLE/COleDropSource::QueryContinueDrag
helpviewer_keywords:
- COleDropSource [MFC], COleDropSource
- COleDropSource [MFC], GiveFeedback
- COleDropSource [MFC], OnBeginDrag
- COleDropSource [MFC], QueryContinueDrag
ms.assetid: d3eecc5f-a70b-4a01-b705-7d2c098ebe17
ms.openlocfilehash: 324c4b7273f021b43c319fb0a494ac843856c78a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375016"
---
# <a name="coledropsource-class"></a>COleDropSource 類別

允許將數據拖動到放置目標。

## <a name="syntax"></a>語法

```
class COleDropSource : public CCmdTarget
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COleDrop 來源:COleDrop 來源](#coledropsource)|建構 `COleDropSource` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleDrop 來源:給回饋](#givefeedback)|在拖放操作期間更改游標。|
|[COleDrop 來源::在BeginDrag](#onbegindrag)|在拖放操作期間處理滑鼠捕獲。|
|[COleDrop 來源::查詢繼續拖動](#querycontinuedrag)|檢查拖動是否應繼續。|

## <a name="remarks"></a>備註

[COleDropTarget](../../mfc/reference/coledroptarget-class.md)類處理拖放操作的接收部分。 對`COleDropSource`象 負責確定拖動操作何時開始,在拖動操作期間提供反饋,並確定拖動操作何時結束。

要使用`COleDropSource`物件,只需調用構造函數。 這簡化了確定哪些事件(如滑鼠按一下)使用[COleDataSource::DoDragDrop、COleClientItem::DoDragDrop](../../mfc/reference/coledatasource-class.md#dodragdrop)[COleClientItem::DoDragDrop](../../mfc/reference/coleclientitem-class.md#dodragdrop)或[COleServerItem::DoDragDrop](../../mfc/reference/coleserveritem-class.md#dodragdrop)函數開始拖動操作的過程。 這些函數將為您創建`COleDropSource`一個物件。 您可能希望修改可重寫函數的`COleDropSource`默認行為。 框架將在適當時間調用這些成員函數。

有關使用 OLE 拖放操作的詳細資訊,請參考文章[OLE 拖放](../../mfc/drag-and-drop-ole.md)。

有關詳細資訊,請參閱 Windows SDK 中的[IDropSource。](/windows/win32/api/oleidl/nn-oleidl-idropsource)

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDropSource`

## <a name="requirements"></a>需求

**標題:** afxole.h

## <a name="coledropsourcecoledropsource"></a><a name="coledropsource"></a>COleDrop 來源:COleDrop 來源

建構 `COleDropSource` 物件。

```
COleDropSource();
```

## <a name="coledropsourcegivefeedback"></a><a name="givefeedback"></a>COleDrop 來源:給回饋

呼叫 COleDropTarget 後由框架呼叫[::onDragover](../../mfc/reference/coledroptarget-class.md#ondragover)或[COleDropTarget::D拉格Enter](../../mfc/reference/coledroptarget-class.md#ondragenter)。

```
virtual SCODE GiveFeedback(DROPEFFECT dropEffect);
```

### <a name="parameters"></a>參數

*滴效果*<br/>
要向使用者顯示的效果,通常指示如果此時與所選數據發生丟棄會發生什麼情況。 通常,這是最近調用[CView 返回的值:OnDragEnter](../../mfc/reference/cview-class.md#ondragenter)或[CView:onDragOver。](../../mfc/reference/cview-class.md#ondragover) 它可以是以下一個或多個:

- DROPEFFECT_NONE不允許掉下。

- DROPEFFECT_COPY將執行複製操作。

- DROPEFFECT_MOVE將執行移動操作。

- DROPEFFECT_LINK將建立從刪除數據到原始數據的連結。

- DROPEFFECT_SCROLL拖動滾動操作即將發生或發生在目標中。

### <a name="return-value"></a>傳回值

如果拖動正在進行,則返回DRAGDROP_S_USEDEFAULTCURSORS;如果沒有,則返回 NOERROR。

### <a name="remarks"></a>備註

重寫此函數,向使用者提供有關此時發生丟棄時將會發生什麼情況的反饋。 預設實現使用 OLE 預設游標。 有關使用 OLE 拖放操作的詳細資訊,請參考文章[OLE 拖放](../../mfc/drag-and-drop-ole.md)。

有關詳細資訊,請參閱[IDropSource::給反饋](/windows/win32/api/oleidl/nf-oleidl-idropsource-givefeedback)[,IDropTarget::DragOver,](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragover)和[IDropTarget::D拉格Enter](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragenter)在 Windows SDK 中。

## <a name="coledropsourceonbegindrag"></a><a name="onbegindrag"></a>COleDrop 來源::在BeginDrag

當可能發生可能開始拖動操作的事件(如按下滑鼠左鍵)時,由框架調用。

```
virtual BOOL OnBeginDrag(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pwnd*<br/>
指向包含所選數據的視窗。

### <a name="return-value"></a>傳回值

如果允許拖動,則不為零,否則為 0。

### <a name="remarks"></a>備註

如果要修改拖動過程的啟動方式,請重寫此函數。 默認實現捕獲滑鼠並保持拖動模式,直到用戶按下滑鼠左鍵或右鍵或按一下 ESC,此時它會釋放滑鼠。

## <a name="coledropsourcequerycontinuedrag"></a><a name="querycontinuedrag"></a>COleDrop 來源::查詢繼續拖動

拖動開始后,框架會反覆調用此函數,直到拖動操作被取消或完成。

```
virtual SCODE QueryContinueDrag(
    BOOL bEscapePressed,
    DWORD dwKeyState);
```

### <a name="parameters"></a>參數

*bEscape壓榨*<br/>
指出自上次調用`COleDropSource::QueryContinueDrag`以來是否按下了 ESC 密鑰。

*德基州*<br/>
包含鍵盤上修改器鍵的狀態。 這是以下任意數量的組合:MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON和MK_RBUTTON。

### <a name="return-value"></a>傳回值

DRAGDROP_S_CANCEL是否按下 ESC 鍵或右鍵,或者在拖動開始之前引發左鍵。 如果應執行放置操作,DRAGDROP_S_DROP。 否則S_OK。

### <a name="remarks"></a>備註

如果要更改取消拖動或放置的點,請覆蓋此函數。

默認實現啟動拖放或取消拖動,如下所示。 按下 ESC 鍵或滑鼠右鍵時,它取消拖動操作。 當滑鼠左鍵在拖動開始后啟動時,它將啟動放置操作。 否則,它將返回S_OK,並且不執行進一步的操作。

由於此函數是頻繁調用的,因此應盡可能對其進行優化。

## <a name="see-also"></a>另請參閱

[MFC 樣品 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[MFC 樣品 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
