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
ms.openlocfilehash: 891b19112c8baf2efb088f064892e1ea19a7deab
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503970"
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
|[COleDropTarget::OnDragEnter](#ondragenter)|在資料指標第一次進入視窗時呼叫。|
|[COleDropTarget::OnDragLeave](#ondragleave)|當資料指標拖曳至視窗外時呼叫。|
|[COleDropTarget::OnDragOver](#ondragover)|將游標拖曳至視窗上方時重複呼叫。|
|[COleDropTarget::OnDragScroll](#ondragscroll)|呼叫以決定是否將游標拖曳至視窗的捲軸區域。|
|[COleDropTarget::OnDrop](#ondrop)|將資料放入視窗、預設處理常式時呼叫。|
|[COleDropTarget::OnDropEx](#ondropex)|將資料放入視窗、初始處理常式時呼叫。|
|[COleDropTarget::Register](#register)|將視窗註冊為有效的放置目標。|
|[COleDropTarget::Revoke](#revoke)|使視窗停止成為有效的放置目標。|

## <a name="remarks"></a>備註

建立這個類別的物件, 可讓視窗透過 OLE 拖放機制接受資料。

若要取得視窗以接受 drop 命令, 您應該先建立`COleDropTarget`類別的物件, 然後以所需`CWnd`物件的指標呼叫[Register](#register)函式做為唯一的參數。

如需有關使用 OLE 拖放作業的詳細資訊, 請參閱[拖放 (OLE)](../../mfc/drag-and-drop-ole.md)一文。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDropTarget`

## <a name="requirements"></a>需求

**標頭:** afxole。h

##  <a name="coledroptarget"></a>  COleDropTarget::COleDropTarget

構造類別`COleDropTarget`的物件。

```
COleDropTarget();
```

### <a name="remarks"></a>備註

呼叫[Register](#register)以將此物件與視窗產生關聯。

##  <a name="ondragenter"></a>  COleDropTarget::OnDragEnter

第一次將游標拖曳至視窗時, 由架構呼叫。

```
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
指向游標所輸入的視窗。

*pDataObject*<br/>
指向包含可以卸載之資料的資料物件。

*dwKeyState*<br/>
包含輔助按鍵的狀態。 這是下列任意數目的組合:MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON 和 MK_RBUTTON。

*point*<br/>
包含目前在用戶端座標中的游標位置。

### <a name="return-value"></a>傳回值

在*point*指定的位置嘗試 drop 時, 會產生的效果。 它可以是下列一或多個:

- 不允許 DROPEFFECT_NONE drop。

- DROPEFFECT_COPY 會執行複製作業。

- DROPEFFECT_MOVE 會執行移動操作。

- DROPEFFECT_LINK 從已卸載的資料到原始資料的連結將會建立。

- DROPEFFECT_SCROLL 拖曳捲軸操作即將發生或發生在目標中。

### <a name="remarks"></a>備註

覆寫此函式, 以允許在視窗中執行 drop 作業。 預設的實值會呼叫[CView:: system.windows.uielement.ondragenter](../../mfc/reference/cview-class.md#ondragenter), 這只會在預設情況下傳回 DROPEFFECT_NONE。

如需詳細資訊, 請參閱 Windows SDK 中的[IDropTarget::D ragenter](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragenter) 。

##  <a name="ondragleave"></a>  COleDropTarget::OnDragLeave

當拖曳操作生效時, 由架構呼叫。

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
指向游標離開的視窗。

### <a name="remarks"></a>備註

如果您想要在拖曳作業離開指定的視窗時有特殊行為, 請覆寫這個函式。 此函式的預設實作用會呼叫[CView:: system.windows.uielement.ondragleave](../../mfc/reference/cview-class.md#ondragleave)。

如需詳細資訊, 請參閱 Windows SDK 中的[IDropTarget::D ragleave](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragleave) 。

##  <a name="ondragover"></a>  COleDropTarget::OnDragOver

當游標拖曳至視窗上方時, 由架構呼叫。

```
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
指向游標停留的視窗。

*pDataObject*<br/>
指向包含要卸載之資料的資料物件。

*dwKeyState*<br/>
包含輔助按鍵的狀態。 這是下列任意數目的組合:MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON 和 MK_RBUTTON。

*point*<br/>
包含目前在用戶端座標中的游標位置。

### <a name="return-value"></a>傳回值

在*point*指定的位置嘗試 drop 時, 會產生的效果。 它可以是下列一或多個:

- 不允許 DROPEFFECT_NONE drop。

- DROPEFFECT_COPY 會執行複製作業。

- DROPEFFECT_MOVE 會執行移動操作。

- DROPEFFECT_LINK 從已卸載的資料到原始資料的連結將會建立。

- DROPEFFECT_SCROLL 表示拖曳捲軸操作即將發生或發生在目標中。

### <a name="remarks"></a>備註

應該覆寫此函式, 以允許在視窗中執行 drop 作業。 此函式的預設實值會呼叫[CView:: system.windows.uielement.ondragover](../../mfc/reference/cview-class.md#ondragover), 它預設會傳回 DROPEFFECT_NONE。 因為此函式會在拖放作業期間經常呼叫, 所以最好盡可能優化。

如需詳細資訊, 請參閱 Windows SDK 中的[IDropTarget::D ragover](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragover) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#21](../../mfc/codesnippet/cpp/coledroptarget-class_1.cpp)]

##  <a name="ondragscroll"></a>  COleDropTarget::OnDragScroll

在呼叫[system.windows.uielement.ondragenter](#ondragenter)或[system.windows.uielement.ondragover](#ondragover)以判斷*點*是否在捲動區域中之前, 由架構呼叫。

```
virtual DROPEFFECT OnDragScroll(
    CWnd* pWnd,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
指向目前游標所在的視窗。

*dwKeyState*<br/>
包含輔助按鍵的狀態。 這是下列任意數目的組合:MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON 和 MK_RBUTTON。

*point*<br/>
包含游標相對於螢幕的位置 (以圖元為單位)。

### <a name="return-value"></a>傳回值

在*point*指定的位置嘗試 drop 時, 會產生的效果。 它可以是下列一或多個:

- 不允許 DROPEFFECT_NONE drop。

- DROPEFFECT_COPY 會執行複製作業。

- DROPEFFECT_MOVE 會執行移動操作。

- DROPEFFECT_LINK 從已卸載的資料到原始資料的連結將會建立。

- DROPEFFECT_SCROLL 表示拖曳捲軸操作即將發生或發生在目標中。

### <a name="remarks"></a>備註

當您想要為此事件提供特殊行為時, 請覆寫此函式。 此函式的預設執行會呼叫[CView:: OnDragScroll](../../mfc/reference/cview-class.md#ondragscroll), 這會傳回 DROPEFFECT_NONE, 並在將游標拖曳至視窗框線內的預設捲動區域時, 滾動視窗。

##  <a name="ondrop"></a>  COleDropTarget::OnDrop

在卸載作業發生時由架構呼叫。

```
virtual BOOL OnDrop(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
指向目前游標所在的視窗。

*pDataObject*<br/>
指向包含要卸載之資料的資料物件。

*dropEffect*<br/>
使用者為 drop 作業選擇的效果。 它可以是下列一或多個:

- DROPEFFECT_COPY 會執行複製作業。

- DROPEFFECT_MOVE 會執行移動操作。

- DROPEFFECT_LINK 從已卸載的資料到原始資料的連結將會建立。

*point*<br/>
包含游標相對於螢幕的位置 (以圖元為單位)。

### <a name="return-value"></a>傳回值

如果卸載成功, 則為非零;否則為0。

### <a name="remarks"></a>備註

架構會先呼叫[OnDropEx](#ondropex)。 如果函式未處理卸載, 架構就會呼叫這個成員`OnDrop`函式。 `OnDropEx` 一般而言, 應用程式會覆寫 view 類別中的[OnDropEx](../../mfc/reference/cview-class.md#ondropex) , 以處理滑鼠右鍵拖放功能。 通常, view 類別[system.windows.uielement.ondrop](../../mfc/reference/cview-class.md#ondrop)是用來處理簡單的拖放。

預設的`COleDropTarget::OnDrop`執行會呼叫[CView:: system.windows.uielement.ondrop](../../mfc/reference/cview-class.md#ondrop), 這只會根據預設傳回 FALSE。

如需詳細資訊, 請參閱 Windows SDK 中的[IDropTarget::D rop](/windows/win32/api/oleidl/nf-oleidl-idroptarget-drop) 。

##  <a name="ondropex"></a>  COleDropTarget::OnDropEx

在卸載作業發生時由架構呼叫。

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
指向目前游標所在的視窗。

*pDataObject*<br/>
指向包含要卸載之資料的資料物件。

*dropDefault*<br/>
根據目前的索引鍵狀態, 使用者為預設的卸載作業所選擇的效果。 它可以是 DROPEFFECT_NONE。 「備註」一節會討論捨棄效果。

*dropList*<br/>
捨棄來源所支援的卸載效果清單。 捨棄效果值可以使用位 OR ( **&#124;** ) 運算來結合。 「備註」一節會討論捨棄效果。

*point*<br/>
包含游標相對於螢幕的位置 (以圖元為單位)。

### <a name="return-value"></a>傳回值

從*point*指定之位置的 drop 嘗試產生的捨棄效果。 「備註」一節會討論捨棄效果。

### <a name="remarks"></a>備註

架構會先呼叫這個函式。 如果它未處理 drop, 則架構會呼叫[system.windows.uielement.ondrop](#ondrop)。 一般來說, 您會覆寫 view 類別中的[OnDropEx](../../mfc/reference/cview-class.md#ondropex) , 以支援滑鼠右鍵拖放功能。 通常, view 類別[system.windows.uielement.ondrop](../../mfc/reference/cview-class.md#ondrop)是用來處理簡單拖放的支援案例。

的預設執行`COleDropTarget::OnDropEx`會呼叫[CView:: OnDropEx](../../mfc/reference/cview-class.md#ondropex)。 根據預設, [CView:: OnDropEx](../../mfc/reference/cview-class.md#ondropex)只會傳回虛擬值, 以指出應該呼叫[system.windows.uielement.ondrop](#ondrop)成員函式。

捨棄效果描述與 drop 作業相關聯的動作。 請參閱下列捨棄效果清單:

- 不允許 DROPEFFECT_NONE drop。

- DROPEFFECT_COPY 會執行複製作業。

- DROPEFFECT_MOVE 會執行移動操作。

- DROPEFFECT_LINK 從已卸載的資料到原始資料的連結將會建立。

- DROPEFFECT_SCROLL 表示拖曳捲軸操作即將發生或發生在目標中。

如需詳細資訊, 請參閱 Windows SDK 中的[IDropTarget::D rop](/windows/win32/api/oleidl/nf-oleidl-idroptarget-drop) 。

##  <a name="register"></a>  COleDropTarget::Register

呼叫此函式可將您的視窗以 OLE Dll 註冊為有效的放置目標。

```
BOOL Register(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
指向要註冊為放置目標的視窗。

### <a name="return-value"></a>傳回值

如果註冊成功, 則為非零值;否則為0。

### <a name="remarks"></a>備註

必須呼叫此函式, 才能接受 drop 作業。

如需詳細資訊, 請參閱 Windows SDK 中的[RegisterDragDrop](/windows/win32/api/ole2/nf-ole2-registerdragdrop) 。

##  <a name="revoke"></a>  COleDropTarget::Revoke

呼叫此函式, 然後透過呼叫[Register](#register)將已註冊為放置目標的任何視窗終結, 以將它從卸載目標清單中移除。

```
virtual void Revoke();
```

### <a name="remarks"></a>備註

系統會針對已註冊的視窗, 從[OnDestroy](../../mfc/reference/cwnd-class.md#ondestroy)處理常式自動呼叫此函式, 因此通常不需要明確呼叫此函式。

如需詳細資訊, 請參閱 Windows SDK 中的[RevokeDragDrop](/windows/win32/api/ole2/nf-ole2-revokedragdrop) 。

## <a name="see-also"></a>另請參閱

[MFC 範例 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[MFC 範例 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleDropSource 類別](../../mfc/reference/coledropsource-class.md)
