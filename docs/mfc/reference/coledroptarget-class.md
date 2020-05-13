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
ms.openlocfilehash: 01eb277da029d06ee44d8e048cf3244f4371a9ec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374998"
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
|[COleDrop目標::COleDrop目標](#coledroptarget)|建構 `COleDropTarget` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleDrop目標::OnDragEnter](#ondragenter)|當游標首次進入視窗時調用。|
|[COleDrop目標::OnDragLeave](#ondragleave)|當游標拖出視窗時調用。|
|[COleDrop目標::OnDragover](#ondragover)|當游標拖過視窗時重複調用。|
|[COleDrop目標::OnDragscroll](#ondragscroll)|呼叫 以確定游標是否拖入視窗的滾動區域。|
|[COleDrop目標::上投](#ondrop)|當數據放入視窗時調用,默認處理程式。|
|[COleDrop目標::OnDropEx](#ondropex)|當數據放入視窗時調用,初始處理程式。|
|[COleDrop目標:: 註冊](#register)|將窗口註冊為有效的放置目標。|
|[COleDrop目標::撤銷](#revoke)|使視窗不再是有效的放置目標。|

## <a name="remarks"></a>備註

創建此類的物件允許視窗通過 OLE 拖放機制接受數據。

要獲取視窗以接受放置命令,應首先創建`COleDropTarget`類的物件,然後使用指向`CWnd`所需 物件的指標調用[Register](#register)函數作為唯一的參數。

有關使用 OLE 拖放操作的詳細資訊,請參考文章[OLE 拖放](../../mfc/drag-and-drop-ole.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDropTarget`

## <a name="requirements"></a>需求

**標題:** afxole.h

## <a name="coledroptargetcoledroptarget"></a><a name="coledroptarget"></a>COleDrop目標::COleDrop目標

建構類別`COleDropTarget`的物件 。

```
COleDropTarget();
```

### <a name="remarks"></a>備註

調用[註冊以](#register)將此物件與視窗關聯。

## <a name="coledroptargetondragenter"></a><a name="ondragenter"></a>COleDrop目標::OnDragEnter

當游標首次拖入視窗時,由框架調用。

```
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>參數

*pwnd*<br/>
指向游標正在輸入的視窗。

*pDataObject*<br/>
指向包含可刪除的數據的數據物件。

*德基州*<br/>
包含修改器鍵的狀態。 這是以下任意數量的組合:MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON和MK_RBUTTON。

*點*<br/>
在用戶端座標中包含游標的當前位置。

### <a name="return-value"></a>傳回值

如果在*點*指定的位置嘗試放置時將導致的效果。 它可以是以下一個或多個:

- DROPEFFECT_NONE不允許掉下。

- DROPEFFECT_COPY將執行複製操作。

- DROPEFFECT_MOVE將執行移動操作。

- DROPEFFECT_LINK將建立從刪除數據到原始數據的連結。

- DROPEFFECT_SCROLL拖動滾動操作即將發生或發生在目標中。

### <a name="remarks"></a>備註

重寫此函數以允許在視窗中執行放置操作。 默認實現調用[CView::onDragEnter](../../mfc/reference/cview-class.md#ondragenter),默認情況下只需返回DROPEFFECT_NONE。

有關詳細資訊,請參閱 Windows SDK 中的[IDropTarget::D拉格 Enter。](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragenter)

## <a name="coledroptargetondragleave"></a><a name="ondragleave"></a>COleDrop目標::OnDragLeave

當游標離開視窗時,當拖動操作生效時,由框架調用。

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pwnd*<br/>
指向游標要離開的視窗。

### <a name="remarks"></a>備註

如果要在拖動操作離開指定視窗時需要特殊行為,請覆蓋此函數。 此函數的預設實現呼叫[CView:onDragLeave](../../mfc/reference/cview-class.md#ondragleave)。

有關詳細資訊,請參閱 Windows SDK 中的[IDropTarget::D拉格離開](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragleave)。

## <a name="coledroptargetondragover"></a><a name="ondragover"></a>COleDrop目標::OnDragover

當游標拖過視窗時,由框架調用。

```
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>參數

*pwnd*<br/>
指向游標已結束的視窗。

*pDataObject*<br/>
指向包含要刪除的數據的數據物件。

*德基州*<br/>
包含修改器鍵的狀態。 這是以下任意數量的組合:MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON和MK_RBUTTON。

*點*<br/>
在用戶端座標中包含游標的當前位置。

### <a name="return-value"></a>傳回值

如果在*點*指定的位置嘗試放置時將導致的效果。 它可以是以下一個或多個:

- DROPEFFECT_NONE不允許掉下。

- DROPEFFECT_COPY將執行複製操作。

- DROPEFFECT_MOVE將執行移動操作。

- DROPEFFECT_LINK將建立從刪除數據到原始數據的連結。

- DROPEFFECT_SCROLL指示拖動滾動操作即將發生或發生在目標中。

### <a name="remarks"></a>備註

應重寫此函數以允許在視窗中執行放置操作。 此函數的預設實現稱為[CView::onDragOver](../../mfc/reference/cview-class.md#ondragover),默認情況下返回DROPEFFECT_NONE。 由於此函數在拖放操作期間頻繁調用,因此應盡可能對其進行優化。

有關詳細資訊,請參閱 Windows SDK 中的[IDropTarget::D拉格。](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragover)

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#21](../../mfc/codesnippet/cpp/coledroptarget-class_1.cpp)]

## <a name="coledroptargetondragscroll"></a><a name="ondragscroll"></a>COleDrop目標::OnDragscroll

在調用[OnDragEnter](#ondragenter)或[OnDragOver](#ondragover)之前由框架調用,以確定*點*是否位於滾動區域中。

```
virtual DROPEFFECT OnDragScroll(
    CWnd* pWnd,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>參數

*pwnd*<br/>
指向游標當前結束的視窗。

*德基州*<br/>
包含修改器鍵的狀態。 這是以下任意數量的組合:MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON和MK_RBUTTON。

*點*<br/>
包含游標相對於螢幕的位置(以像素為單位)。

### <a name="return-value"></a>傳回值

如果在*點*指定的位置嘗試放置時將導致的效果。 它可以是以下一個或多個:

- DROPEFFECT_NONE不允許掉下。

- DROPEFFECT_COPY將執行複製操作。

- DROPEFFECT_MOVE將執行移動操作。

- DROPEFFECT_LINK將建立從刪除數據到原始數據的連結。

- DROPEFFECT_SCROLL指示拖動滾動操作即將發生或發生在目標中。

### <a name="remarks"></a>備註

如果要為此事件提供特殊行為,請重寫此函數。 此函數的預設實現稱為[CView::OnDragScroll](../../mfc/reference/cview-class.md#ondragscroll),當游標拖動到視窗邊框內的預設滾動區域時,它返回DROPEFFECT_NONE並滾動視窗。

## <a name="coledroptargetondrop"></a><a name="ondrop"></a>COleDrop目標::上投

當發生放置操作時,由框架調用。

```
virtual BOOL OnDrop(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>參數

*pwnd*<br/>
指向游標當前結束的視窗。

*pDataObject*<br/>
指向包含要刪除的數據的數據物件。

*滴效果*<br/>
用戶為放置操作選擇的效果。 它可以是以下一個或多個:

- DROPEFFECT_COPY將執行複製操作。

- DROPEFFECT_MOVE將執行移動操作。

- DROPEFFECT_LINK將建立從刪除數據到原始數據的連結。

*點*<br/>
包含游標相對於螢幕的位置(以像素為單位)。

### <a name="return-value"></a>傳回值

如果丟棄成功,則非零;否則 0。

### <a name="remarks"></a>備註

框架首先呼叫[OnDropEx](#ondropex)。 如果`OnDropEx`函數不處理丟棄,則框架將呼叫此成員函`OnDrop`數 。 通常,應用程式將覆蓋檢視類中的[OnDropEx,](../../mfc/reference/cview-class.md#ondropex)以處理滑鼠右鍵拖放。 通常,視圖類[OnDrop](../../mfc/reference/cview-class.md#ondrop)用於處理簡單的拖放。

調用`COleDropTarget::OnDrop`[CView::onDrop](../../mfc/reference/cview-class.md#ondrop)的預設實現,默認情況下只需返回 FALSE。

有關詳細資訊,請參閱 Windows SDK 中的[IDropTarget::Drop。](/windows/win32/api/oleidl/nf-oleidl-idroptarget-drop)

## <a name="coledroptargetondropex"></a><a name="ondropex"></a>COleDrop目標::OnDropEx

當發生放置操作時,由框架調用。

```
virtual DROPEFFECT OnDropEx(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropDefault,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>參數

*pwnd*<br/>
指向游標當前結束的視窗。

*pDataObject*<br/>
指向包含要刪除的數據的數據物件。

*丟棄預設*<br/>
使用者根據當前鍵狀態為預設放置操作選擇的效果。 它可以DROPEFFECT_NONE。 「註釋」部分將討論放置效果。

*下拉清單*<br/>
放置來源支援的放置效果的清單。 可以使用位或 **(&#124;**) 操作組合放置效果值。 「註釋」部分將討論放置效果。

*點*<br/>
包含游標相對於螢幕的位置(以像素為單位)。

### <a name="return-value"></a>傳回值

從*點指定的位置*的放置嘗試產生的放置效果。 「註釋」部分將討論放置效果。

### <a name="remarks"></a>備註

框架首先調用此函數。 如果它不處理丟棄,則框架將呼叫[OnDrop](#ondrop)。 通常,您將在檢視類中覆蓋[OnDropEx](../../mfc/reference/cview-class.md#ondropex)以支援滑鼠右鍵拖放。 通常,視圖類[OnDrop](../../mfc/reference/cview-class.md#ondrop)用於處理支援簡單拖放的情況。

呼叫 CView`COleDropTarget::OnDropEx`預設[:onDropEx](../../mfc/reference/cview-class.md#ondropex)。 默認情況下[,CView:onDropEx](../../mfc/reference/cview-class.md#ondropex)僅返回一個虛擬值,以指示應調用[OnDrop](#ondrop)成員函數。

放置效果描述與放置操作關聯的操作。 請參考以下放置效果清單:

- DROPEFFECT_NONE不允許掉下。

- DROPEFFECT_COPY將執行複製操作。

- DROPEFFECT_MOVE將執行移動操作。

- DROPEFFECT_LINK將建立從刪除數據到原始數據的連結。

- DROPEFFECT_SCROLL指示拖動滾動操作即將發生或發生在目標中。

有關詳細資訊,請參閱 Windows SDK 中的[IDropTarget::Drop。](/windows/win32/api/oleidl/nf-oleidl-idroptarget-drop)

## <a name="coledroptargetregister"></a><a name="register"></a>COleDrop目標:: 註冊

調用此函數以將窗口註冊為有效的放置目標。

```
BOOL Register(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pwnd*<br/>
指向要註冊為放置目標的視窗。

### <a name="return-value"></a>傳回值

註冊成功時非零;否則 0。

### <a name="remarks"></a>備註

必須調用此函數才能接受放置操作。

有關詳細資訊,請參閱 Windows SDK 中的[註冊DragDrop。](/windows/win32/api/ole2/nf-ole2-registerdragdrop)

## <a name="coledroptargetrevoke"></a><a name="revoke"></a>COleDrop目標::撤銷

在通過「[註冊」](#register)調用銷毀已註冊為放置目標的任何視窗之前調用此函數,以便將其從放置目標清單中刪除。

```
virtual void Revoke();
```

### <a name="remarks"></a>備註

此函數從已註冊視窗的[On銷毀](../../mfc/reference/cwnd-class.md#ondestroy)處理程式自動調用,因此通常不需要顯式調用此函數。

有關詳細資訊,請參閱 Windows SDK 中的[「撤銷DragDrop」。。](/windows/win32/api/ole2/nf-ole2-revokedragdrop)

## <a name="see-also"></a>另請參閱

[MFC 樣品 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[MFC 樣品 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleDropSource 類別](../../mfc/reference/coledropsource-class.md)
