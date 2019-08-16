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
ms.openlocfilehash: 3a1e27ca6c1019eb8716194b3b7711238d015d6d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503993"
---
# <a name="coledropsource-class"></a>COleDropSource 類別

允許將資料拖曳至放置目標。

## <a name="syntax"></a>語法

```
class COleDropSource : public CCmdTarget
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[COleDropSource::COleDropSource](#coledropsource)|建構 `COleDropSource` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[COleDropSource::GiveFeedback](#givefeedback)|在拖放作業期間變更游標。|
|[COleDropSource::OnBeginDrag](#onbegindrag)|在拖放作業期間處理滑鼠捕捉。|
|[COleDropSource::QueryContinueDrag](#querycontinuedrag)|檢查是否應該繼續拖曳。|

## <a name="remarks"></a>備註

[COleDropTarget](../../mfc/reference/coledroptarget-class.md)類別會處理拖放作業的接收部分。 `COleDropSource`物件負責判斷拖曳作業開始的時間、在拖曳作業期間提供意見反應, 以及判斷拖曳作業結束的時間。

若要使用`COleDropSource`物件, 只要呼叫此函式即可。 這可簡化判斷哪些事件 (例如按一下滑鼠), 使用[COleDataSource::D odragdrop](../../mfc/reference/coledatasource-class.md#dodragdrop)、 [COleClientItem::D odragdrop](../../mfc/reference/coleclientitem-class.md#dodragdrop)或[COleServerItem::D odragdrop](../../mfc/reference/coleserveritem-class.md#dodragdrop)函數來開始拖曳作業的程式。 這些函式會為`COleDropSource`您建立物件。 您可能想要修改可覆`COleDropSource`寫函式的預設行為。 架構會在適當的時間呼叫這些成員函式。

如需有關使用 OLE 拖放作業的詳細資訊, 請參閱[拖放 (OLE)](../../mfc/drag-and-drop-ole.md)一文。

如需詳細資訊, 請參閱 Windows SDK 中的[IDropSource](/windows/win32/api/oleidl/nn-oleidl-idropsource) 。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDropSource`

## <a name="requirements"></a>需求

**標頭:** afxole。h

##  <a name="coledropsource"></a>COleDropSource::COleDropSource

建構 `COleDropSource` 物件。

```
COleDropSource();
```

##  <a name="givefeedback"></a>COleDropSource:: System.windows.dragdrop.givefeedback>

在呼叫[COleDropTarget:: system.windows.uielement.ondragover](../../mfc/reference/coledroptarget-class.md#ondragover)或[COleDropTarget::D ragenter](../../mfc/reference/coledroptarget-class.md#ondragenter)之後, 由架構呼叫。

```
virtual SCODE GiveFeedback(DROPEFFECT dropEffect);
```

### <a name="parameters"></a>參數

*dropEffect*<br/>
您想要對使用者顯示的效果, 通常會指出在此時間點發生含有選取的資料時, 會發生什麼事。 一般來說, 這是最新的[CView:: system.windows.uielement.ondragenter](../../mfc/reference/cview-class.md#ondragenter)或[Cview:: system.windows.uielement.ondragover](../../mfc/reference/cview-class.md#ondragover)呼叫所傳回的值。 它可以是下列一或多個:

- 不允許 DROPEFFECT_NONE drop。

- DROPEFFECT_COPY 會執行複製作業。

- DROPEFFECT_MOVE 會執行移動操作。

- DROPEFFECT_LINK 從已卸載的資料到原始資料的連結將會建立。

- DROPEFFECT_SCROLL 拖曳捲軸操作即將發生或發生在目標中。

### <a name="return-value"></a>傳回值

如果拖曳正在進行中, 則會傳回 DRAGDROP_S_USEDEFAULTCURSORS, 如果不是, 則傳回 AAD-USERREADUSINGALTERNATIVESECURITYID-NOERROR。

### <a name="remarks"></a>備註

覆寫此函式, 以向使用者提供意見反應, 以瞭解此時是否會發生這種情況。 預設的執行會使用 OLE 預設資料指標。 如需有關使用 OLE 拖放作業的詳細資訊, 請參閱[拖放 (OLE)](../../mfc/drag-and-drop-ole.md)一文。

如需詳細資訊, 請參閱 Windows SDK 中的[IDropSource:: system.windows.dragdrop.givefeedback>](/windows/win32/api/oleidl/nf-oleidl-idropsource-givefeedback)、 [IDropTarget::D ragover](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragover)和[IDropTarget::D ragenter](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragenter) 。

##  <a name="onbegindrag"></a>COleDropSource::OnBeginDrag

當發生可能開始拖曳作業的事件 (例如按下滑鼠左鍵) 時, 由架構呼叫。

```
virtual BOOL OnBeginDrag(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
指向包含所選取資料的視窗。

### <a name="return-value"></a>傳回值

如果允許拖曳, 則為非零, 否則為0。

### <a name="remarks"></a>備註

如果您想要修改拖曳進程的啟動方式, 請覆寫此函式。 預設的執行會捕捉滑鼠並停留在拖曳模式中, 直到使用者按一下滑鼠左鍵或滑鼠右鍵, 或按 ESC 鍵, 此時會放開滑鼠。

##  <a name="querycontinuedrag"></a>COleDropSource:: System.windows.dragdrop.querycontinuedrag>

開始拖曳之後, 架構會重複呼叫此函式, 直到拖曳作業取消或完成為止。

```
virtual SCODE QueryContinueDrag(
    BOOL bEscapePressed,
    DWORD dwKeyState);
```

### <a name="parameters"></a>參數

*bEscapePressed*<br/>
指出自上次呼叫`COleDropSource::QueryContinueDrag`之後是否已按下 ESC 鍵。

*dwKeyState*<br/>
包含鍵盤上輔助按鍵的狀態。 這是下列任意數目的組合:MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON 和 MK_RBUTTON。

### <a name="return-value"></a>傳回值

DRAGDROP_S_CANCEL, 如果按下 ESC 鍵或右鍵, 或在拖曳開始前引發左按鈕。 DRAGDROP_S_DROP 是否應執行 DROP 作業。 否則為 S_OK。

### <a name="remarks"></a>備註

如果您想要變更取消拖曳或卸載的時間點, 請覆寫這個函式。

預設的執行會起始 drop 或取消拖曳, 如下所示。 當按下 ESC 鍵或滑鼠右鍵時, 它會取消拖曳作業。 它會在拖曳開始後引發滑鼠左鍵時, 起始 drop 作業。 否則, 它會傳回 S_OK, 而且不會執行任何進一步的作業。

因為此函式是經常呼叫的, 所以應該盡可能優化。

## <a name="see-also"></a>另請參閱

[MFC 範例 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[MFC 範例 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
