---
title: COleDropTarget 類別
ms.date: 11/04/2016
f1_keywords:
- COleDropTarget
- AFXOLE/COleDropTarget
- AFXOLE/COleDropTarget::COleDropTarget
- AFXOLE/COleDropTarget::OnDragEnter
- AFXOLE/COleDropTarget::OnDragLeave
- AFXOLE/COleDropTarget::OnDragOver
- AFXOLE/COleDropTarget::OnDragScroll
- AFXOLE/COleDropTarget::OnDrop
- AFXOLE/COleDropTarget::OnDropEx
- AFXOLE/COleDropTarget::Register
- AFXOLE/COleDropTarget::Revoke
helpviewer_keywords:
- COleDropTarget [MFC], COleDropTarget
- COleDropTarget [MFC], OnDragEnter
- COleDropTarget [MFC], OnDragLeave
- COleDropTarget [MFC], OnDragOver
- COleDropTarget [MFC], OnDragScroll
- COleDropTarget [MFC], OnDrop
- COleDropTarget [MFC], OnDropEx
- COleDropTarget [MFC], Register
- COleDropTarget [MFC], Revoke
ms.assetid: a58c9a48-6a93-4357-b078-4594df258311
ms.openlocfilehash: 9a1633ed48c763b986f3421c33589a05f8bba126
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58781636"
---
# <a name="coledroptarget-class"></a>COleDropTarget 類別

提供視窗與 OLE 程式庫之間的溝通機制。

## <a name="syntax"></a>語法

```
class COleDropTarget : public CCmdTarget
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COleDropTarget::COleDropTarget](#coledroptarget)|建構 `COleDropTarget` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleDropTarget::OnDragEnter](#ondragenter)|當游標第一次進入視窗時呼叫。|
|[COleDropTarget::OnDragLeave](#ondragleave)|當資料指標拖曳出視窗時呼叫。|
|[COleDropTarget::OnDragOver](#ondragover)|當資料指標拖曳到視窗時重複呼叫。|
|[COleDropTarget::OnDragScroll](#ondragscroll)|呼叫以判斷是否要將資料指標拖曳至視窗的捲軸的區域。|
|[COleDropTarget::OnDrop](#ondrop)|當資料放入視窗中，預設處理常式時呼叫。|
|[COleDropTarget::OnDropEx](#ondropex)|當資料放入視窗中，初始的處理常式時呼叫。|
|[COleDropTarget::Register](#register)|暫存器視窗，以做為有效的置放目標。|
|[COleDropTarget::Revoke](#revoke)|會使視窗停止正在有效的置放目標。|

## <a name="remarks"></a>備註

建立此類別的物件，可讓一個視窗，以透過 OLE 拖放機制接受資料。

若要取得可接受拖放命令視窗，您應該先建立的物件`COleDropTarget`類別，然後再呼叫[註冊](#register)函式的指標，所要使用`CWnd`物件做為唯一的參數。

如需有關拖放作業使用 OLE，請參閱文章[拖放 (OLE)](../../mfc/drag-and-drop-ole.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDropTarget`

## <a name="requirements"></a>需求

**標頭：** afxole.h

##  <a name="coledroptarget"></a>  COleDropTarget::COleDropTarget

建構的物件類別`COleDropTarget`。

```
COleDropTarget();
```

### <a name="remarks"></a>備註

呼叫[註冊](#register)這個物件相關聯的視窗。

##  <a name="ondragenter"></a>  COleDropTarget::OnDragEnter

當游標第一次拖曳到視窗時，由架構呼叫。

```
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
輸入到視窗資料指標的點。

*pDataObject*<br/>
加入資料物件，其中包含可以卸除的資料點。

*dwKeyState*<br/>
包含的輔助按鍵的狀態。 這是任意數目的下列組合：MK_CONTROL、 MK_SHIFT、 MK_ALT、 MK_LBUTTON、 MK_MBUTTON 和 MK_RBUTTON。

*point*<br/>
包含工作區座標中的資料指標的目前的位置。

### <a name="return-value"></a>傳回值

如果嘗試卸除所指定的位置而造成的效果*點*。 它可以是下列其中一個或多個項目：

- DROPEFFECT_NONE 不會允許卸除。

- DROPEFFECT_COPY 執行複製作業。

- DROPEFFECT_MOVE 會執行移動作業。

- 會建立已卸除的資料從原始資料的 DROPEFFECT_LINK 的連結。

- DROPEFFECT_SCROLL A 拖曳捲軸作業會發生，或在目標中進行。

### <a name="remarks"></a>備註

覆寫這個函式，允許發生在視窗中的拖放作業。 預設實作會呼叫[CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter)，它只會傳回 DROPEFFECT_NONE 預設。

如需詳細資訊，請參閱 < [IDropTarget::DragEnter](/windows/desktop/api/oleidl/nf-oleidl-idroptarget-dragenter) Windows SDK 中。

##  <a name="ondragleave"></a>  COleDropTarget::OnDragLeave

當游標離開視窗拖曳作業生效時，由架構呼叫。

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
指向視窗離開資料指標。

### <a name="remarks"></a>備註

如果您想要特殊的行為，拖放作業離開指定的視窗時，請覆寫這個函式。 此函式的預設實作會呼叫[CView::OnDragLeave](../../mfc/reference/cview-class.md#ondragleave)。

如需詳細資訊，請參閱 < [IDropTarget::DragLeave](/windows/desktop/api/oleidl/nf-oleidl-idroptarget-dragleave) Windows SDK 中。

##  <a name="ondragover"></a>  COleDropTarget::OnDragOver

當資料指標拖曳到視窗時，由架構呼叫。

```
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
游標位於視窗的點。

*pDataObject*<br/>
指向包含要卸除之資料的資料物件。

*dwKeyState*<br/>
包含的輔助按鍵的狀態。 這是任意數目的下列組合：MK_CONTROL、 MK_SHIFT、 MK_ALT、 MK_LBUTTON、 MK_MBUTTON 和 MK_RBUTTON。

*point*<br/>
包含工作區座標中的資料指標的目前的位置。

### <a name="return-value"></a>傳回值

如果嘗試卸除所指定的位置而造成的效果*點*。 它可以是下列其中一個或多個項目：

- DROPEFFECT_NONE 不會允許卸除。

- DROPEFFECT_COPY 執行複製作業。

- DROPEFFECT_MOVE 會執行移動作業。

- 會建立已卸除的資料從原始資料的 DROPEFFECT_LINK 的連結。

- DROPEFFECT_SCROLL 表示拖曳捲軸作業會發生，或在目標中進行。

### <a name="remarks"></a>備註

應該覆寫這個函式，以允許發生在視窗中的拖放作業。 此函式的預設實作會呼叫[CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover)，它會傳回 DROPEFFECT_NONE 預設。 拖放作業期間經常會呼叫此函數，因為它應該最佳化盡量。

如需詳細資訊，請參閱 < [IDropTarget::DragOver](/windows/desktop/api/oleidl/nf-oleidl-idroptarget-dragover) Windows SDK 中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#21](../../mfc/codesnippet/cpp/coledroptarget-class_1.cpp)]

##  <a name="ondragscroll"></a>  COleDropTarget::OnDragScroll

由架構呼叫之前，先呼叫[OnDragEnter](#ondragenter)或是[OnDragOver](#ondragover)以判斷是否*點*捲軸的區域中。

```
virtual DROPEFFECT OnDragScroll(
    CWnd* pWnd,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
游標位於目前視窗的點。

*dwKeyState*<br/>
包含的輔助按鍵的狀態。 這是任意數目的下列組合：MK_CONTROL、 MK_SHIFT、 MK_ALT、 MK_LBUTTON、 MK_MBUTTON 和 MK_RBUTTON。

*point*<br/>
包含的資料指標，像素為單位，相對於畫面的位置。

### <a name="return-value"></a>傳回值

如果嘗試卸除所指定的位置而造成的效果*點*。 它可以是下列其中一個或多個項目：

- DROPEFFECT_NONE 不會允許卸除。

- DROPEFFECT_COPY 執行複製作業。

- DROPEFFECT_MOVE 會執行移動作業。

- 會建立已卸除的資料從原始資料的 DROPEFFECT_LINK 的連結。

- DROPEFFECT_SCROLL 表示拖曳捲軸作業會發生，或在目標中進行。

### <a name="remarks"></a>備註

當您想要提供特殊的行為，這個事件時，請覆寫這個函式。 此函式的預設實作會呼叫[CView::OnDragScroll](../../mfc/reference/cview-class.md#ondragscroll)，這會傳回 DROPEFFECT_NONE 和捲動視窗，當資料指標拖曳到視窗的框線中的預設捲動區域。

##  <a name="ondrop"></a>  COleDropTarget::OnDrop

卸除作業發生時，由架構呼叫。

```
virtual BOOL OnDrop(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
游標位於目前視窗的點。

*pDataObject*<br/>
指向包含要卸除之資料的資料物件。

*dropEffect*<br/>
使用者選擇拖放作業效果。 它可以是下列其中一個或多個項目：

- DROPEFFECT_COPY 執行複製作業。

- DROPEFFECT_MOVE 會執行移動作業。

- 會建立已卸除的資料從原始資料的 DROPEFFECT_LINK 的連結。

*point*<br/>
包含的資料指標，像素為單位，相對於畫面的位置。

### <a name="return-value"></a>傳回值

如果成功，卸除，非零值。否則為 0。

### <a name="remarks"></a>備註

架構先呼叫[OnDropEx](#ondropex)。 如果`OnDropEx`函式不會處理卸除，然後架構會呼叫此成員函式， `OnDrop`。 一般而言，應用程式會覆寫[OnDropEx](../../mfc/reference/cview-class.md#ondropex)來處理滑鼠右鍵的 view 類別中將拖放。 通常，檢視類別[OnDrop](../../mfc/reference/cview-class.md#ondrop)用來處理簡單的拖放和 drop。

預設實作`COleDropTarget::OnDrop`呼叫[CView::OnDrop](../../mfc/reference/cview-class.md#ondrop)，這只是預設會傳回 FALSE。

如需詳細資訊，請參閱 < [IDropTarget::Drop](/windows/desktop/api/oleidl/nf-oleidl-idroptarget-drop) Windows SDK 中。

##  <a name="ondropex"></a>  COleDropTarget::OnDropEx

卸除作業發生時，由架構呼叫。

```
virtual DROPEFFECT OnDropEx(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropDefault,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
游標位於目前視窗的點。

*pDataObject*<br/>
指向包含要卸除之資料的資料物件。

*dropDefault*<br/>
使用者選擇針對根據目前的索引鍵狀態預設拖放作業效果。 它可以是 DROPEFFECT_NONE。 置放效果是 < 備註 > 一節所述。

*dropList*<br/>
拖曳來源所支援的拖放效果的清單。 可以使用的位元 OR 組合置放效果值 (**&#124;**) 作業。 置放效果是 < 備註 > 一節所述。

*point*<br/>
包含的資料指標，像素為單位，相對於畫面的位置。

### <a name="return-value"></a>傳回值

卸除嘗試在所指定的位置產生的置放效果*點*。 置放效果是 < 備註 > 一節所述。

### <a name="remarks"></a>備註

架構會先呼叫此函式。 如果未處理的拖放，架構會呼叫[OnDrop](#ondrop)。 一般而言，您將會覆寫[OnDropEx](../../mfc/reference/cview-class.md#ondropex)中的檢視類別，以支援滑鼠右鍵將拖放。 通常，檢視類別[OnDrop](../../mfc/reference/cview-class.md#ondrop)用來處理簡單的拖放和拖放支援的大小寫。

預設實作`COleDropTarget::OnDropEx`呼叫[CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex)。 根據預設， [CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex)只會傳回空的值，指出[OnDrop](#ondrop)應該呼叫成員函式。

置放效果描述與拖放作業相關聯的動作。 請參閱下列清單中的拖放效果：

- DROPEFFECT_NONE 不會允許卸除。

- DROPEFFECT_COPY 執行複製作業。

- DROPEFFECT_MOVE 會執行移動作業。

- 會建立已卸除的資料從原始資料的 DROPEFFECT_LINK 的連結。

- DROPEFFECT_SCROLL 表示拖曳捲軸作業會發生，或在目標中進行。

如需詳細資訊，請參閱 < [IDropTarget::Drop](/windows/desktop/api/oleidl/nf-oleidl-idroptarget-drop) Windows SDK 中。

##  <a name="register"></a>  COleDropTarget::Register

呼叫此函式可註冊您的視窗與 OLE Dll 做為有效的置放目標。

```
BOOL Register(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
指向要做為置放目標註冊的視窗。

### <a name="return-value"></a>傳回值

如果註冊成功則為非零否則為 0。

### <a name="remarks"></a>備註

此函式必須呼叫接受拖放作業。

如需詳細資訊，請參閱 < [RegisterDragDrop](/windows/desktop/api/ole2/nf-ole2-registerdragdrop) Windows SDK 中。

##  <a name="revoke"></a>  COleDropTarget::Revoke

呼叫此函式之前終結鴢做為置放目標，透過呼叫任何視窗[註冊](#register)移除置放目標的清單。

```
virtual void Revoke();
```

### <a name="remarks"></a>備註

從自動呼叫此函式[OnDestroy](../../mfc/reference/cwnd-class.md#ondestroy)已註冊，因此通常不需要明確呼叫此函式之視窗的處理常式。

如需詳細資訊，請參閱 < [RevokeDragDrop](/windows/desktop/api/ole2/nf-ole2-revokedragdrop) Windows SDK 中。

## <a name="see-also"></a>另請參閱

[MFC 範例 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[MFC 範例 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleDropSource 類別](../../mfc/reference/coledropsource-class.md)
