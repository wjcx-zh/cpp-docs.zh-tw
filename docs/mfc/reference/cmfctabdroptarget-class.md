---
title: CMFCTabDropTarget 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCTabDropTarget
- AFXBASETABCTRL/CMFCTabDropTarget
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragEnter
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragLeave
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragOver
- AFXBASETABCTRL/CMFCTabDropTarget::OnDropEx
- AFXBASETABCTRL/CMFCTabDropTarget::Register
helpviewer_keywords:
- CMFCTabDropTarget [MFC], OnDragEnter
- CMFCTabDropTarget [MFC], OnDragLeave
- CMFCTabDropTarget [MFC], OnDragOver
- CMFCTabDropTarget [MFC], OnDropEx
- CMFCTabDropTarget [MFC], Register
ms.assetid: 9777b7b6-10da-4c4b-b1d1-7ea795b0f1cb
ms.openlocfilehash: 83432fdb90fe28214fb1faaf843556deb2f44750
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367349"
---
# <a name="cmfctabdroptarget-class"></a>CMFCTabDropTarget 類別

提供選項卡控制件和OLE庫之間的通訊機制。

## <a name="syntax"></a>語法

```
class CMFCTabDropTarget : public COleDropTarget
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|||
|-|-|
|名稱|描述|
|`CMFCTabDropTarget::CMFCTabDropTarget`|預設建構函式。|

### <a name="public-methods"></a>公用方法

|||
|-|-|
|名稱|描述|
|[CMFCTabDrop目標::onDragenter](#ondragenter)|當使用者將物件拖動到選項卡視窗中時,由框架調用。 (覆蓋[COleDrop 目標::OnDragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter).)|
|[CMFCTabDrop目標::OnDragLeave](#ondragleave)|當使用者在具有焦點的選項卡視窗外拖動物件時,由框架調用。 (覆蓋[COleDrop 目標::OnDragLeave](../../mfc/reference/coledroptarget-class.md#ondragleave).)|
|[CMFCTabDrop目標::OnDragover](#ondragover)|當使用者將物件拖動到具有焦點的選項卡視窗時,由框架調用。 (覆蓋[COleDrop 目標::OnDragover.)](../../mfc/reference/coledroptarget-class.md#ondragover)|
|[CMFCTabDrop目標::OnDropEx](#ondropex)|當使用者在拖動操作結束時釋放滑鼠按鈕時,由框架調用。 (覆寫[COleDrop 目標:onDropEx](../../mfc/reference/coledroptarget-class.md#ondropex).)|
|[CMFCTabDrop目標::註冊](#register)|將控制項註冊為可作為 OLE 拖放操作目標的控制項。|

### <a name="remarks"></a>備註

此類為`CMFCBaseTabCtrl`類提供拖放支援。 如果應用程式使用[AfxOleInit](ole-initialization.md#afxoleinit)函數初始化 OLE 庫,`CMFCBaseTabCtrl`則物件將自行註冊以執行拖放操作。

當`CMFCTabDropTarget`拖動操作發生活動時,類通過使游標下方的選項卡變為活動來擴展其基類。 有關拖放操作的詳細資訊,請參閱[OLE 拖放](../../mfc/drag-and-drop-ole.md)操作 。

## <a name="example"></a>範例

下列範例示範如何建構 `CMFCTabDropTarget` 物件及使用其 `Register` 方法。

[!code-cpp[NVC_MFC_RibbonApp#39](../../mfc/reference/codesnippet/cpp/cmfctabdroptarget-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[COleDropTarget](../../mfc/reference/coledroptarget-class.md)

[CMFCTabDrop目標](../../mfc/reference/cmfctabdroptarget-class.md)

## <a name="requirements"></a>需求

**標頭：** afxbasetabctrl.h

## <a name="cmfctabdroptargetondragenter"></a><a name="ondragenter"></a>CMFCTabDrop目標::onDragenter

當使用者將物件拖動到選項卡視窗中時,由框架調用。

```
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*pwnd*|[在]閑置。|
|*pDataObject*|[在]指向使用者拖動的物件的指標。|
|*德基州*|[在]包含修改器鍵的狀態。 這是以下任意數量的組合:MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON和MK_RBUTTON。|
|*點*|[在]游標在客戶端座標中的位置。|

### <a name="return-value"></a>傳回值

如果放置發生在*點*指定的位置,則產生的效果。 它可以是以下一個或多個:

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>備註

如果工具列框架未處於自訂模式或剪貼簿數據格式不可用,則此方法將返回DROPEFFECT_NONE。 否則,它將返回使用提供的參數調用`CMFCBaseTabCtrl::OnDragEnter`的結果。

有關自訂模式的詳細資訊,請參閱[CMFCToolBar::是自訂模式](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)。 關於剪貼簿資料格式的詳細資訊,請參考[COleDataObject::是資料可用](../../mfc/reference/coledataobject-class.md#isdataavailable)。

## <a name="cmfctabdroptargetondragleave"></a><a name="ondragleave"></a>CMFCTabDrop目標::OnDragLeave

當使用者在具有焦點的選項卡視窗外拖動物件時,由框架調用。

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*pwnd*|[在]閑置。|

### <a name="remarks"></a>備註

此方法調用`CMFCBaseTabCtrl::OnDragLeave`方法 以執行拖動操作。

## <a name="cmfctabdroptargetondragover"></a><a name="ondragover"></a>CMFCTabDrop目標::OnDragover

當使用者將物件拖動到具有焦點的選項卡視窗時,由框架調用。

```
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*pwnd*|[在]閑置。|
|*pDataObject*|[在]指向使用者拖動的物件的指標。|
|*德基州*|[在]包含修改器鍵的狀態。 這是以下任意數量的組合:MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON和MK_RBUTTON。|
|*點*|[在]滑鼠指標在客戶端座標中的位置。|

### <a name="return-value"></a>傳回值

如果放置發生在*點*指定的位置,則產生的效果。 它可以是以下一個或多個:

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>備註

此方法使拖動操作發生時光標下方的選項卡處於活動狀態。 如果工具列框架未處於自定義模式或剪貼簿數據格式不可用,則返回DROPEFFECT_NONE。 否則,它將返回使用提供的參數調用`CMFCBaseTabCtrl::OnDragOver`的結果。

有關自訂模式的詳細資訊,請參閱[CMFCToolBar::是自訂模式](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)。 關於剪貼簿資料格式的詳細資訊,請參考[COleDataObject::是資料可用](../../mfc/reference/coledataobject-class.md#isdataavailable)。

## <a name="cmfctabdroptargetondropex"></a><a name="ondropex"></a>CMFCTabDrop目標::OnDropEx

當使用者在拖動操作結束時釋放滑鼠按鈕時,由框架調用。

```
virtual DROPEFFECT OnDropEx(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*pwnd*|[在]閑置。|
|*pDataObject*|[在]指向使用者拖動的物件的指標。|
|*滴效果*|[在]默認放置操作。|
|*下拉清單*|[在]閑置。|
|*點*|[在]滑鼠指標在客戶端座標中的位置。|

### <a name="return-value"></a>傳回值

生成的放置效果。 它可以是以下一個或多個:

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>備註

如果工具列框架`CMFCBaseTabCtrl::OnDrop`處於自定義模式且剪貼簿數據格式可用,則此方法將調用。 如果調用返回`CMFCBaseTabCtrl::OnDrop`非零值,此方法將返回*drop效果*指定的預設刪除效果。 否則,此方法將返回DROPEFFECT_NONE。 有關放置效果的詳細資訊,請參閱[COleDropTarget::onDropEx](../../mfc/reference/coledroptarget-class.md#ondropex)。

有關自訂模式的詳細資訊,請參閱[CMFCToolBar::是自訂模式](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)。 關於剪貼簿資料格式的詳細資訊,請參考[COleDataObject::是資料可用](../../mfc/reference/coledataobject-class.md#isdataavailable)。

## <a name="cmfctabdroptargetregister"></a><a name="register"></a>CMFCTabDrop目標::註冊

將控制項註冊為可作為 OLE 拖放操作目標的控制項。

```
BOOL Register(CMFCBaseTabCtrl *pOwner);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*pOwner*|[在]要註冊為放置目標的選項卡控制項。|

### <a name="return-value"></a>傳回值

註冊成功時非零;否則 0。

### <a name="remarks"></a>備註

此方法調用[COleDropTarget::註冊](../../mfc/reference/coledroptarget-class.md#register)以註冊拖放操作的控制項。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[OLE 拖放](../../mfc/drag-and-drop-ole.md)
