---
title: "COleDropTarget 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- COleDropTarget class
- drag and drop, drop target
- drop commands, accepting
- drop commands
ms.assetid: a58c9a48-6a93-4357-b078-4594df258311
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 0e9429d531d6af86bc571b1f871fbcd4a8fe2532
ms.lasthandoff: 02/24/2017

---
# <a name="coledroptarget-class"></a>COleDropTarget 類別
提供視窗與 OLE 程式庫之間的溝通機制。  
  
## <a name="syntax"></a>語法  
  
```  
class COleDropTarget : public CCmdTarget  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[COleDropTarget::COleDropTarget](#coledroptarget)|建構 `COleDropTarget` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[COleDropTarget::OnDragEnter](#ondragenter)|資料指標第一次進入視窗時呼叫。|  
|[COleDropTarget::OnDragLeave](#ondragleave)|資料指標拖曳出視窗時呼叫。|  
|[COleDropTarget::OnDragOver](#ondragover)|當游標拖曳到視窗時重複呼叫。|  
|[COleDropTarget::OnDragScroll](#ondragscroll)|呼叫以判斷是否要將資料指標拖曳至捲動視窗的區域。|  
|[COleDropTarget::OnDrop](#ondrop)|當資料放入 視窗中，預設處理常式時呼叫。|  
|[COleDropTarget::OnDropEx](#ondropex)|當資料放入 視窗中，初始的處理常式時呼叫。|  
|[COleDropTarget::Register](#register)|暫存器視窗，以做為有效的置放目標。|  
|[COleDropTarget::Revoke](#revoke)|會停止正在有效的置放目標視窗。|  
  
## <a name="remarks"></a>備註  
 建立這個類別的物件，讓透過 OLE 拖放機制接受資料的視窗。  
  
 若要取得接受 drop 命令視窗，您應該先建立的物件`COleDropTarget`類別，並接著呼叫[註冊](#register)函式指標指向所需的`CWnd`物件做為唯一參數。  
  
 如需有關拖放作業使用 OLE，請參閱文章[拖放 (OLE)](../../mfc/drag-and-drop-ole.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleDropTarget`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxole.h  
  
##  <a name="coledroptarget"></a>COleDropTarget::COleDropTarget  
 建構類別的物件`COleDropTarget`。  
  
```  
COleDropTarget();
```  
  
### <a name="remarks"></a>備註  
 呼叫[註冊](#register)此物件關聯的視窗。  
  
##  <a name="ondragenter"></a>COleDropTarget::OnDragEnter  
 當資料指標第一次拖曳到視窗時，由架構呼叫。  
  
```  
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>參數  
 `pWnd`  
 正在進入點至視窗資料指標。  
  
 `pDataObject`  
 包含要卸除之資料的資料物件的指標。  
  
 `dwKeyState`  
 包含輔助按鍵的狀態。 這是下列任何數目的組合︰ **MK_CONTROL**， **MK_SHIFT**， **MK_ALT**， **MK_LBUTTON**， **MK_MBUTTON**，和**MK_RBUTTON**。  
  
 `point`  
 包含用戶端座標中的資料指標目前位置。  
  
### <a name="return-value"></a>傳回值  
 卸除已嘗試在所指定的位置時，會產生的效果`point`。 它可以是下列一或多項動作︰  
  
- `DROPEFFECT_NONE`不會允許置放。  
  
- `DROPEFFECT_COPY`執行複製作業。  
  
- `DROPEFFECT_MOVE`會執行移動作業。  
  
- `DROPEFFECT_LINK`會建立原始資料的連結從卸除的資料。  
  
- `DROPEFFECT_SCROLL`拖曳捲軸作業即將發生或發生在目標中。  
  
### <a name="remarks"></a>備註  
 覆寫此函式可允許拖放作業，才會發生在視窗中。 預設實作會呼叫[CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter)，它只會傳回`DROPEFFECT_NONE`預設。  
  
 如需詳細資訊，請參閱[IDropTarget::DragEnter](http://msdn.microsoft.com/library/windows/desktop/ms680106)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="ondragleave"></a>COleDropTarget::OnDragLeave  
 由架構呼叫時，游標離開視窗拖曳作業時生效。  
  
```  
virtual void OnDragLeave(CWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 `pWnd`  
 指向視窗的游標離開。  
  
### <a name="remarks"></a>備註  
 如果您想在拖曳作業離開指定的視窗時的特殊行為，請覆寫這個函式。 此函式的預設實作會呼叫[CView::OnDragLeave](../../mfc/reference/cview-class.md#ondragleave)。  
  
 如需詳細資訊，請參閱[IDropTarget::DragLeave](http://msdn.microsoft.com/library/windows/desktop/ms680110)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="ondragover"></a>COleDropTarget::OnDragOver  
 將游標拖曳到視窗時，由架構呼叫。  
  
```  
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>參數  
 `pWnd`  
 游標位於視窗的指標。  
  
 `pDataObject`  
 資料物件，其中包含要卸除的資料點。  
  
 `dwKeyState`  
 包含輔助按鍵的狀態。 這是下列任何數目的組合︰ **MK_CONTROL**， **MK_SHIFT**， **MK_ALT**， **MK_LBUTTON**， **MK_MBUTTON**，和**MK_RBUTTON**。  
  
 `point`  
 包含用戶端座標中的資料指標目前位置。  
  
### <a name="return-value"></a>傳回值  
 卸除已嘗試在所指定的位置時，會產生的效果`point`。 它可以是下列一或多項動作︰  
  
- `DROPEFFECT_NONE`不會允許置放。  
  
- `DROPEFFECT_COPY`執行複製作業。  
  
- `DROPEFFECT_MOVE`會執行移動作業。  
  
- `DROPEFFECT_LINK`會建立原始資料的連結從卸除的資料。  
  
- `DROPEFFECT_SCROLL`表示拖曳捲軸作業即將發生或發生在目標中。  
  
### <a name="remarks"></a>備註  
 此函式應該覆寫，以允許拖放作業，才會發生在視窗中。 此函式的預設實作會呼叫[CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover)，它會傳回`DROPEFFECT_NONE`預設。 在拖放作業期間經常會呼叫此函數，因為它應該最佳化儘可能。  
  
 如需詳細資訊，請參閱[IDropTarget::DragOver](http://msdn.microsoft.com/library/windows/desktop/ms680129)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer #&21;](../../mfc/codesnippet/cpp/coledroptarget-class_1.cpp)]  
  
##  <a name="ondragscroll"></a>COleDropTarget::OnDragScroll  
 然後再呼叫架構呼叫[OnDragEnter](#ondragenter)或[OnDragOver](#ondragover)來判斷是否`point`捲動區域中。  
  
```  
virtual DROPEFFECT OnDragScroll(
    CWnd* pWnd,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>參數  
 `pWnd`  
 游標位於目前視窗的指標。  
  
 `dwKeyState`  
 包含輔助按鍵的狀態。 這是下列任何數目的組合︰ **MK_CONTROL**， **MK_SHIFT**， **MK_ALT**， **MK_LBUTTON**， **MK_MBUTTON**，和**MK_RBUTTON**。  
  
 `point`  
 包含的資料指標，相對於螢幕像素為單位的位置。  
  
### <a name="return-value"></a>傳回值  
 卸除已嘗試在所指定的位置時，會產生的效果`point`。 它可以是下列一或多項動作︰  
  
- `DROPEFFECT_NONE`不會允許置放。  
  
- `DROPEFFECT_COPY`執行複製作業。  
  
- `DROPEFFECT_MOVE`會執行移動作業。  
  
- `DROPEFFECT_LINK`會建立原始資料的連結從卸除的資料。  
  
- `DROPEFFECT_SCROLL`表示拖曳捲軸作業即將發生或發生在目標中。  
  
### <a name="remarks"></a>備註  
 當您想要針對此事件提供特殊行為時，覆寫這個函式。 此函式的預設實作會呼叫[CView::OnDragScroll](../../mfc/reference/cview-class.md#ondragscroll)，它會傳回`DROPEFFECT_NONE`和捲動資料指標拖曳至視窗的框線的預設捲動區域時的視窗。  
  
##  <a name="ondrop"></a>COleDropTarget::OnDrop  
 卸除作業發生時，由架構呼叫。  
  
```  
virtual BOOL OnDrop(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DROPEFFECT dropEffect,  
    CPoint point);
```  
  
### <a name="parameters"></a>參數  
 `pWnd`  
 游標位於目前視窗的指標。  
  
 `pDataObject`  
 資料物件，其中包含要卸除的資料點。  
  
 `dropEffect`  
 使用者選擇拖放作業效果。 它可以是下列一或多項動作︰  
  
- `DROPEFFECT_COPY`執行複製作業。  
  
- `DROPEFFECT_MOVE`會執行移動作業。  
  
- `DROPEFFECT_LINK`會建立原始資料的連結從卸除的資料。  
  
 `point`  
 包含的資料指標，相對於螢幕像素為單位的位置。  
  
### <a name="return-value"></a>傳回值  
 如果卸除成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 架構會先呼叫[OnDropEx](#ondropex)。 如果`OnDropEx`函式不會處理卸除，然後架構會呼叫此成員函式， `OnDrop`。 一般而言，應用程式會覆寫[OnDropEx](../../mfc/reference/cview-class.md#ondropex)中檢視類別來處理滑鼠右鍵拖曳和卸除。 通常，檢視類別[OnDrop](../../mfc/reference/cview-class.md#ondrop)用來處理簡單拖曳和卸除。  
  
 預設實作`COleDropTarget::OnDrop`呼叫[CView::OnDrop](../../mfc/reference/cview-class.md#ondrop)，它只會傳回**FALSE**預設。  
  
 如需詳細資訊，請參閱[IDropTarget::Drop](http://msdn.microsoft.com/library/windows/desktop/ms687242)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="ondropex"></a>COleDropTarget::OnDropEx  
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
 `pWnd`  
 游標位於目前視窗的指標。  
  
 `pDataObject`  
 資料物件，其中包含要卸除的資料點。  
  
 `dropDefault`  
 使用者選擇根據索引鍵的目前狀態的預設拖放作業效果。 它可以是`DROPEFFECT_NONE`。 < 備註 > 一節中討論的置放效果。  
  
 `dropList`  
 卸除來源支援拖放效果的清單。 可以使用的位元 OR 合併置放效果值 ( **|**) 作業。 < 備註 > 一節中討論的置放效果。  
  
 `point`  
 包含的資料指標，相對於螢幕像素為單位的位置。  
  
### <a name="return-value"></a>傳回值  
 卸除嘗試在所指定的位置所產生的置放效果`point`。 < 備註 > 一節中討論的置放效果。  
  
### <a name="remarks"></a>備註  
 架構會先呼叫此函式。 如果它不會處理卸除，架構會呼叫[OnDrop](#ondrop)。 一般而言，您將會覆寫[OnDropEx](../../mfc/reference/cview-class.md#ondropex)中的檢視類別，以支援滑鼠右鍵拖曳和卸除。 通常，檢視類別[OnDrop](../../mfc/reference/cview-class.md#ondrop)用來處理的簡單儲存拖放支援的情況。  
  
 預設實作`COleDropTarget::OnDropEx`呼叫[CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex)。 根據預設， [CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex)只會傳回空值，指出[OnDrop](#ondrop)應該呼叫成員函式。  
  
 置放效果會描述與拖放作業相關聯的動作。 請參閱下列置放效果的清單︰  
  
- `DROPEFFECT_NONE`不會允許置放。  
  
- `DROPEFFECT_COPY`執行複製作業。  
  
- `DROPEFFECT_MOVE`會執行移動作業。  
  
- `DROPEFFECT_LINK`會建立原始資料的連結從卸除的資料。  
  
- `DROPEFFECT_SCROLL`表示拖曳捲軸作業即將發生或發生在目標中。  
  
 如需詳細資訊，請參閱[IDropTarget::Drop](http://msdn.microsoft.com/library/windows/desktop/ms687242)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="register"></a>COleDropTarget::Register  
 呼叫此函式可註冊您的視窗與 OLE Dll 做為有效的置放目標。  
  
```  
BOOL Register(CWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 `pWnd`  
 指向以登錄為置放目標的視窗。  
  
### <a name="return-value"></a>傳回值  
 如果註冊成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 此函式必須接受拖放作業的呼叫。  
  
 如需詳細資訊，請參閱[RegisterDragDrop](http://msdn.microsoft.com/library/windows/desktop/ms678405)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="revoke"></a>COleDropTarget::Revoke  
 呼叫此函式，然後再終結登錄為置放目標，透過呼叫的任何視窗[註冊](#register)若要移除的置放目標清單。  
  
```  
virtual void Revoke();
```  
  
### <a name="remarks"></a>備註  
 從自動呼叫此函式[OnDestroy](../../mfc/reference/cwnd-class.md#ondestroy)已註冊，因此通常不需要明確呼叫此函式 視窗的處理常式。  
  
 如需詳細資訊，請參閱[RevokeDragDrop](http://msdn.microsoft.com/library/windows/desktop/ms692643)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 HIERSVR](../../visual-cpp-samples.md)   
 [MFC 範例 OCLIENT](../../visual-cpp-samples.md)   
 [CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleDropSource 類別](../../mfc/reference/coledropsource-class.md)

