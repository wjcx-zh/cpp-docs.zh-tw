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
ms.openlocfilehash: d0090386b1ebb4d89b9a7613a0b2a28529decbe5
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127424"
---
# <a name="cmfctabdroptarget-class"></a>CMFCTabDropTarget 類別

提供索引標籤控制項和 OLE 程式庫之間的通訊機制。

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
|[CMFCTabDropTarget：： System.windows.uielement.ondragenter](#ondragenter)|當使用者將物件拖曳到索引標籤視窗時由架構呼叫。 （覆寫[COleDropTarget：： system.windows.uielement.ondragenter](../../mfc/reference/coledroptarget-class.md#ondragenter)。）|
|[CMFCTabDropTarget：： System.windows.uielement.ondragleave](#ondragleave)|當使用者在具有焦點的索引標籤視窗外拖曳物件時，由架構呼叫。 （覆寫[COleDropTarget：： system.windows.uielement.ondragleave](../../mfc/reference/coledroptarget-class.md#ondragleave)。）|
|[CMFCTabDropTarget：： System.windows.uielement.ondragover](#ondragover)|當使用者將物件拖曳至具有焦點的索引標籤視窗上時，由架構呼叫。 （覆寫[COleDropTarget：： system.windows.uielement.ondragover](../../mfc/reference/coledroptarget-class.md#ondragover)。）|
|[CMFCTabDropTarget::OnDropEx](#ondropex)|當使用者在拖曳作業結束時放開滑鼠按鍵時，由架構呼叫。 （覆寫[COleDropTarget：： OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex)。）|
|[CMFCTabDropTarget：： Register](#register)|將控制項註冊為可做為 OLE 拖放作業目標的控制項。|

### <a name="remarks"></a>備註

這個類別會提供 `CMFCBaseTabCtrl` 類別的拖放支援。 如果您的應用程式使用[AfxOleInit](ole-initialization.md#afxoleinit)函式初始化 OLE 程式庫，`CMFCBaseTabCtrl` 物件會自行註冊以進行拖放作業。

`CMFCTabDropTarget` 類別藉由在拖曳作業發生時，讓游標下的索引標籤延伸其基類。 如需拖放作業的詳細資訊，請參閱[OLE 拖放](../../mfc/drag-and-drop-ole.md)。

## <a name="example"></a>範例

下列範例示範如何建構 `CMFCTabDropTarget` 物件及使用其 `Register` 方法。

[!code-cpp[NVC_MFC_RibbonApp#39](../../mfc/reference/codesnippet/cpp/cmfctabdroptarget-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[COleDropTarget](../../mfc/reference/coledroptarget-class.md)

[CMFCTabDropTarget](../../mfc/reference/cmfctabdroptarget-class.md)

## <a name="requirements"></a>需求

**標頭：** afxbasetabctrl.h

##  <a name="ondragenter"></a>CMFCTabDropTarget：： System.windows.uielement.ondragenter

當使用者將物件拖曳到索引標籤視窗時由架構呼叫。

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
|*pWnd*|在未使用.|
|*pDataObject*|在使用者拖曳之物件的指標。|
|*dwKeyState*|在包含輔助按鍵的狀態。 這是下列任意數目的組合： MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON 和 MK_RBUTTON。|
|*此處*|在資料指標在用戶端座標中的位置。|

### <a name="return-value"></a>傳回值

當卸載發生在*point*指定的位置時，所產生的效果。 它可以是下列一或多個：

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>備註

如果工具列架構不是處於自訂模式，或剪貼簿資料格式無法使用，這個方法會傳回 DROPEFFECT_NONE。 否則，它會傳回使用提供的參數呼叫 `CMFCBaseTabCtrl::OnDragEnter` 的結果。

如需自訂模式的詳細資訊，請參閱[CMFCToolBar：： IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)。 如需剪貼簿資料格式的詳細資訊，請參閱[COleDataObject：： IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable)。

##  <a name="ondragleave"></a>CMFCTabDropTarget：： System.windows.uielement.ondragleave

當使用者在具有焦點的索引標籤視窗外拖曳物件時，由架構呼叫。

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*pWnd*|在未使用.|

### <a name="remarks"></a>備註

這個方法會呼叫 `CMFCBaseTabCtrl::OnDragLeave` 方法來執行拖曳作業。

##  <a name="ondragover"></a>CMFCTabDropTarget：： System.windows.uielement.ondragover

當使用者將物件拖曳至具有焦點的索引標籤視窗上時，由架構呼叫。

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
|*pWnd*|在未使用.|
|*pDataObject*|在使用者拖曳之物件的指標。|
|*dwKeyState*|在包含輔助按鍵的狀態。 這是下列任意數目的組合： MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON 和 MK_RBUTTON。|
|*此處*|在滑鼠指標在用戶端座標中的位置。|

### <a name="return-value"></a>傳回值

當卸載發生在*point*指定的位置時，所產生的效果。 它可以是下列一或多個：

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>備註

當拖曳作業發生在使用中時，這個方法會讓位於游標下的索引標籤。 如果工具列架構不是處於自訂模式，或剪貼簿資料格式無法使用，它會傳回 DROPEFFECT_NONE。 否則，它會傳回使用提供的參數呼叫 `CMFCBaseTabCtrl::OnDragOver` 的結果。

如需自訂模式的詳細資訊，請參閱[CMFCToolBar：： IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)。 如需剪貼簿資料格式的詳細資訊，請參閱[COleDataObject：： IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable)。

##  <a name="ondropex"></a>CMFCTabDropTarget::OnDropEx

當使用者在拖曳作業結束時放開滑鼠按鍵時，由架構呼叫。

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
|*pWnd*|在未使用.|
|*pDataObject*|在使用者拖曳之物件的指標。|
|*dropEffect*|在預設的 drop 作業。|
|*dropList*|在未使用.|
|*此處*|在滑鼠指標在用戶端座標中的位置。|

### <a name="return-value"></a>傳回值

產生的捨棄效果。 它可以是下列一或多個：

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>備註

如果工具列架構處於自訂模式，而且有可用的剪貼簿資料格式，則這個方法會呼叫 `CMFCBaseTabCtrl::OnDrop`。 如果 `CMFCBaseTabCtrl::OnDrop` 的呼叫傳回非零值，這個方法會傳回*dropEffect*所指定的預設 drop 效果。 否則，這個方法會傳回 DROPEFFECT_NONE。 如需捨棄效果的詳細資訊，請參閱[COleDropTarget：： OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex)。

如需自訂模式的詳細資訊，請參閱[CMFCToolBar：： IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)。 如需剪貼簿資料格式的詳細資訊，請參閱[COleDataObject：： IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable)。

##  <a name="register"></a>CMFCTabDropTarget：： Register

將控制項註冊為可做為 OLE 拖放作業目標的控制項。

```
BOOL Register(CMFCBaseTabCtrl *pOwner);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*pOwner*|在要註冊為放置目標的索引標籤控制項。|

### <a name="return-value"></a>傳回值

如果註冊成功，則為非零;否則為0。

### <a name="remarks"></a>備註

這個方法會呼叫[COleDropTarget：： register](../../mfc/reference/coledroptarget-class.md#register)來註冊拖放作業的控制項。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[OLE 拖放](../../mfc/drag-and-drop-ole.md)
