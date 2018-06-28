---
title: COleDropTarget 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fec20d8bb960d48392f2d174dab9ee6497738c80
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37039598"
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
|[COleDropTarget::OnDragLeave](#ondragleave)|當游標拖出視窗時呼叫。|  
|[COleDropTarget::OnDragOver](#ondragover)|當游標拖曳到視窗時重複呼叫。|  
|[COleDropTarget::OnDragScroll](#ondragscroll)|呼叫以判斷是否要將資料指標拖曳至視窗的捲軸區域。|  
|[COleDropTarget::OnDrop](#ondrop)|當資料放入視窗中，預設處理常式時呼叫。|  
|[COleDropTarget::OnDropEx](#ondropex)|當資料放入視窗中，初始的處理常式時呼叫。|  
|[COleDropTarget::Register](#register)|暫存器視窗，以做為有效的置放目標。|  
|[COleDropTarget::Revoke](#revoke)|會造成視窗也會停止正在的有效置放目標。|  
  
## <a name="remarks"></a>備註  
 建立這個類別的物件，可讓透過 OLE 拖放機制接受資料的視窗。  
  
 若要取得接受 drop 命令視窗，您應該先建立的物件`COleDropTarget`類別，然後再呼叫[註冊](#register)函式的指標所需`CWnd`物件做為唯一參數。  
  
 如需拖放作業使用 OLE，請參閱文章[拖放 (OLE)](../../mfc/drag-and-drop-ole.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleDropTarget`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxole.h  
  
##  <a name="coledroptarget"></a>  COleDropTarget::COleDropTarget  
 會建構一個物件類別的`COleDropTarget`。  
  
```  
COleDropTarget();
```  
  
### <a name="remarks"></a>備註  
 呼叫[註冊](#register)將此物件與視窗產生關聯。  
  
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
 *pWnd*  
 正在進入點至視窗資料指標。  
  
 *pDataObject*  
 指向包含要卸除之資料的資料物件。  
  
 *dwKeyState*  
 包含輔助按鍵的狀態。 這是任意數目的下列組合： **MK_CONTROL**， **MK_SHIFT**， **MK_ALT**， **MK_LBUTTON**， **MK_MBUTTON**，和**MK_RBUTTON**。  
  
 *點*  
 包含用戶端座標中的資料指標的目前位置。  
  
### <a name="return-value"></a>傳回值  
 卸除已嘗試在所指定的位置時，會產生的效果*點*。 它可以是下列一或多個項目：  
  
- `DROPEFFECT_NONE` 不允許卸除。  
  
- `DROPEFFECT_COPY` 執行複製作業。  
  
- `DROPEFFECT_MOVE` 會執行移動作業。  
  
- `DROPEFFECT_LINK` 會建立已卸除的資料從原始資料的連結。  
  
- `DROPEFFECT_SCROLL` 拖曳捲軸作業即將發生或正在進行中的目標。  
  
### <a name="remarks"></a>備註  
 覆寫此函式可允許拖放作業，才會發生在視窗中。 預設實作會呼叫[CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter)，它只會傳回`DROPEFFECT_NONE`預設。  
  
 如需詳細資訊，請參閱[IDropTarget::DragEnter](http://msdn.microsoft.com/library/windows/desktop/ms680106) Windows SDK 中。  
  
##  <a name="ondragleave"></a>  COleDropTarget::OnDragLeave  
 當游標離開視窗拖曳作業時作用中時，由架構呼叫。  
  
```  
virtual void OnDragLeave(CWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 *pWnd*  
 指向視窗游標離開。  
  
### <a name="remarks"></a>備註  
 如果您想要的特殊行為拖曳作業會保留指定的視窗，請覆寫這個函式。 此函式的預設實作會呼叫[CView::OnDragLeave](../../mfc/reference/cview-class.md#ondragleave)。  
  
 如需詳細資訊，請參閱[IDropTarget::DragLeave](http://msdn.microsoft.com/library/windows/desktop/ms680110) Windows SDK 中。  
  
##  <a name="ondragover"></a>  COleDropTarget::OnDragOver  
 當游標拖曳到視窗時，由架構呼叫。  
  
```  
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>參數  
 *pWnd*  
 游標位於視窗的點。  
  
 *pDataObject*  
 指向包含要卸除之資料的資料物件。  
  
 *dwKeyState*  
 包含輔助按鍵的狀態。 這是任意數目的下列組合： **MK_CONTROL**， **MK_SHIFT**， **MK_ALT**， **MK_LBUTTON**， **MK_MBUTTON**，和**MK_RBUTTON**。  
  
 *點*  
 包含用戶端座標中的資料指標的目前位置。  
  
### <a name="return-value"></a>傳回值  
 卸除已嘗試在所指定的位置時，會產生的效果*點*。 它可以是下列一或多個項目：  
  
- `DROPEFFECT_NONE` 不允許卸除。  
  
- `DROPEFFECT_COPY` 執行複製作業。  
  
- `DROPEFFECT_MOVE` 會執行移動作業。  
  
- `DROPEFFECT_LINK` 會建立已卸除的資料從原始資料的連結。  
  
- `DROPEFFECT_SCROLL` 表示即將發生拖曳捲軸作業，或目標中發生的狀況。  
  
### <a name="remarks"></a>備註  
 應該覆寫這個函式，以允許拖放作業，才會發生在視窗中。 此函式的預設實作會呼叫[CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover)，它會傳回`DROPEFFECT_NONE`預設。 因為經常在拖放作業期間會呼叫此函數，它應該最佳化盡量。  
  
 如需詳細資訊，請參閱[IDropTarget::DragOver](http://msdn.microsoft.com/library/windows/desktop/ms680129) Windows SDK 中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer#21](../../mfc/codesnippet/cpp/coledroptarget-class_1.cpp)]  
  
##  <a name="ondragscroll"></a>  COleDropTarget::OnDragScroll  
 由架構呼叫之前呼叫[OnDragEnter](#ondragenter)或[OnDragOver](#ondragover)來判斷是否*點*捲軸的區域中。  
  
```  
virtual DROPEFFECT OnDragScroll(
    CWnd* pWnd,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>參數  
 *pWnd*  
 指向資料指標位於目前的視窗。  
  
 *dwKeyState*  
 包含輔助按鍵的狀態。 這是任意數目的下列組合： **MK_CONTROL**， **MK_SHIFT**， **MK_ALT**， **MK_LBUTTON**， **MK_MBUTTON**，和**MK_RBUTTON**。  
  
 *點*  
 包含資料指標，以像素與相對螢幕的位置。  
  
### <a name="return-value"></a>傳回值  
 卸除已嘗試在所指定的位置時，會產生的效果*點*。 它可以是下列一或多個項目：  
  
- `DROPEFFECT_NONE` 不允許卸除。  
  
- `DROPEFFECT_COPY` 執行複製作業。  
  
- `DROPEFFECT_MOVE` 會執行移動作業。  
  
- `DROPEFFECT_LINK` 會建立已卸除的資料從原始資料的連結。  
  
- `DROPEFFECT_SCROLL` 表示即將發生拖曳捲軸作業，或目標中發生的狀況。  
  
### <a name="remarks"></a>備註  
 當您想要提供特殊的行為，這個事件時，覆寫這個函式。 此函式的預設實作會呼叫[CView::OnDragScroll](../../mfc/reference/cview-class.md#ondragscroll)，它會傳回`DROPEFFECT_NONE`和捲動資料指標拖曳至視窗的框線的預設捲軸區域時的視窗。  
  
##  <a name="ondrop"></a>  COleDropTarget::OnDrop  
 進行拖放作業時，由架構呼叫。  
  
```  
virtual BOOL OnDrop(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DROPEFFECT dropEffect,  
    CPoint point);
```  
  
### <a name="parameters"></a>參數  
 *pWnd*  
 指向資料指標位於目前的視窗。  
  
 *pDataObject*  
 指向包含要卸除之資料的資料物件。  
  
 *dropEffect*  
 使用者選擇拖放作業的效果。 它可以是下列一或多個項目：  
  
- `DROPEFFECT_COPY` 執行複製作業。  
  
- `DROPEFFECT_MOVE` 會執行移動作業。  
  
- `DROPEFFECT_LINK` 會建立已卸除的資料從原始資料的連結。  
  
 *點*  
 包含資料指標，以像素與相對螢幕的位置。  
  
### <a name="return-value"></a>傳回值  
 卸除成功; 如果為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 架構先呼叫[OnDropEx](#ondropex)。 如果`OnDropEx`函式不會處理下拉式清單，然後架構會呼叫此成員函式， `OnDrop`。 一般而言，應用程式會覆寫[OnDropEx](../../mfc/reference/cview-class.md#ondropex)處理滑鼠右鍵在檢視類別中拖曳和卸除。 通常，檢視類別[OnDrop](../../mfc/reference/cview-class.md#ondrop)用來處理簡單拖曳和卸除。  
  
 預設實作`COleDropTarget::OnDrop`呼叫[CView::OnDrop](../../mfc/reference/cview-class.md#ondrop)，它只會傳回**FALSE**預設。  
  
 如需詳細資訊，請參閱[IDropTarget::Drop](http://msdn.microsoft.com/library/windows/desktop/ms687242) Windows SDK 中。  
  
##  <a name="ondropex"></a>  COleDropTarget::OnDropEx  
 進行拖放作業時，由架構呼叫。  
  
```  
virtual DROPEFFECT OnDropEx(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DROPEFFECT dropDefault,  
    DROPEFFECT dropList,  
    CPoint point);
```  
  
### <a name="parameters"></a>參數  
 *pWnd*  
 指向資料指標位於目前的視窗。  
  
 *pDataObject*  
 指向包含要卸除之資料的資料物件。  
  
 *dropDefault*  
 使用者選擇根據索引鍵的目前狀態的預設拖放作業的效果。 它可以是`DROPEFFECT_NONE`。 < 備註 > 一節中討論的置放效果。  
  
 *下拉清單*  
 置放來源支援置放效果的清單。 可以使用的位元 OR 結合置放效果值 ( **&#124;**) 作業。 < 備註 > 一節中討論的置放效果。  
  
 *點*  
 包含資料指標，以像素與相對螢幕的位置。  
  
### <a name="return-value"></a>傳回值  
 卸除嘗試在所指定的位置所產生的置放效果*點*。 < 備註 > 一節中討論的置放效果。  
  
### <a name="remarks"></a>備註  
 架構會先呼叫此函式。 如果它不會處理卸除，架構會呼叫[OnDrop](#ondrop)。 一般而言，您將會覆寫[OnDropEx](../../mfc/reference/cview-class.md#ondropex)中檢視類別，以支援滑鼠右鍵拖曳和卸除。 通常，檢視類別[OnDrop](../../mfc/reference/cview-class.md#ondrop)用來處理支援簡單拖曳和卸除的大小寫。  
  
 預設實作`COleDropTarget::OnDropEx`呼叫[CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex)。 根據預設， [CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex)只會傳回空值，指出[OnDrop](#ondrop)應該呼叫成員函式。  
  
 拖放效果描述與拖放作業相關聯的動作。 請參閱下列置放效果的清單：  
  
- `DROPEFFECT_NONE` 不允許卸除。  
  
- `DROPEFFECT_COPY` 執行複製作業。  
  
- `DROPEFFECT_MOVE` 會執行移動作業。  
  
- `DROPEFFECT_LINK` 會建立已卸除的資料從原始資料的連結。  
  
- `DROPEFFECT_SCROLL` 表示即將發生拖曳捲軸作業，或目標中發生的狀況。  
  
 如需詳細資訊，請參閱[IDropTarget::Drop](http://msdn.microsoft.com/library/windows/desktop/ms687242) Windows SDK 中。  
  
##  <a name="register"></a>  COleDropTarget::Register  
 呼叫此函式可註冊您的視窗與 OLE Dll 做為有效的置放目標。  
  
```  
BOOL Register(CWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 *pWnd*  
 指向以登錄為置放目標的視窗。  
  
### <a name="return-value"></a>傳回值  
 如果登錄成功，則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 此函式必須接受拖放作業的呼叫。  
  
 如需詳細資訊，請參閱[RegisterDragDrop](http://msdn.microsoft.com/library/windows/desktop/ms678405) Windows SDK 中。  
  
##  <a name="revoke"></a>  COleDropTarget::Revoke  
 呼叫此函式之前終結登錄為置放目標，透過呼叫任何視窗[註冊](#register)移除從置放目標的清單。  
  
```  
virtual void Revoke();
```  
  
### <a name="remarks"></a>備註  
 從自動呼叫此函式[OnDestroy](../../mfc/reference/cwnd-class.md#ondestroy)已登錄，因此通常不需要明確呼叫此函式之視窗的處理常式。  
  
 如需詳細資訊，請參閱[RevokeDragDrop](http://msdn.microsoft.com/library/windows/desktop/ms692643) Windows SDK 中。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 HIERSVR](../../visual-cpp-samples.md)   
 [MFC 範例 OCLIENT](../../visual-cpp-samples.md)   
 [CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleDropSource 類別](../../mfc/reference/coledropsource-class.md)
