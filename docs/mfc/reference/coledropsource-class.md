---
title: "COleDropSource 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleDropSource
- AFXOLE/COleDropSource
- AFXOLE/COleDropSource::COleDropSource
- AFXOLE/COleDropSource::GiveFeedback
- AFXOLE/COleDropSource::OnBeginDrag
- AFXOLE/COleDropSource::QueryContinueDrag
dev_langs:
- C++
helpviewer_keywords:
- drag operations
- drop target, dragging data to
- COleDropSource class
- drag and drop, drop source
ms.assetid: d3eecc5f-a70b-4a01-b705-7d2c098ebe17
caps.latest.revision: 24
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: f3d0e5b7184cf305459173065b8e1cc07e032aef
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="coledropsource-class"></a>COleDropSource 類別
允許將資料拖曳到置放目標。  
  
## <a name="syntax"></a>語法  
  
```  
class COleDropSource : public CCmdTarget  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[COleDropSource::COleDropSource](#coledropsource)|建構 `COleDropSource` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[COleDropSource::GiveFeedback](#givefeedback)|拖放作業期間變更資料指標。|  
|[COleDropSource::OnBeginDrag](#onbegindrag)|拖放作業期間處理滑鼠捕捉。|  
|[COleDropSource::QueryContinueDrag](#querycontinuedrag)|會查看拖曳是否應該繼續執行。|  
  
## <a name="remarks"></a>備註  
 [COleDropTarget](../../mfc/reference/coledroptarget-class.md)類別會處理拖放作業的接收部分。 `COleDropSource`物件負責決定何時開始拖曳作業、 提供意見反應拖曳作業期間，以及決定拖曳作業結束時。  
  
 若要使用`COleDropSource`物件，只需要呼叫建構函式。 這可簡化程序可決定哪些事件，例如按一下滑鼠開始拖曳作業使用[COleDataSource::DoDragDrop](../../mfc/reference/coledatasource-class.md#dodragdrop)， [COleClientItem::DoDragDrop](../../mfc/reference/coleclientitem-class.md#dodragdrop)，或[COleServerItem::DoDragDrop](../../mfc/reference/coleserveritem-class.md#dodragdrop)函式。 這些函式會建立`COleDropSource`為您的物件。 您可能想要修改的預設行為`COleDropSource`可覆寫函式。 由架構，這些成員函式會在適當時間呼叫。  
  
 如需有關拖放作業使用 OLE，請參閱文章[拖放 (OLE)](../../mfc/drag-and-drop-ole.md)。  
  
 如需詳細資訊，請參閱[IDropSource](http://msdn.microsoft.com/library/windows/desktop/ms690071)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleDropSource`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxole.h  
  
##  <a name="coledropsource"></a>COleDropSource::COleDropSource  
 建構 `COleDropSource` 物件。  
  
```  
COleDropSource();
```  
  
##  <a name="givefeedback"></a>COleDropSource::GiveFeedback  
 在呼叫之後，由框架呼叫[COleDropTarget::OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover)或[COleDropTarget::DragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter)。  
  
```  
virtual SCODE GiveFeedback(DROPEFFECT dropEffect);
```  
  
### <a name="parameters"></a>參數  
 `dropEffect`  
 您想要向使用者顯示的效果，通常表示什麼會發生置放在與所選取的資料為止。 一般而言，這是最新的呼叫所傳回的值[CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter)或[CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover)。 它可以是下列一或多項動作︰  
  
- `DROPEFFECT_NONE`不會允許置放。  
  
- `DROPEFFECT_COPY`執行複製作業。  
  
- `DROPEFFECT_MOVE`會執行移動作業。  
  
- `DROPEFFECT_LINK`會建立原始資料的連結從卸除的資料。  
  
- `DROPEFFECT_SCROLL`拖曳捲軸作業即將發生或發生在目標中。  
  
### <a name="return-value"></a>傳回值  
 傳回**DRAGDROP_S_USEDEFAULTCURSORS**如果已在進行中，拖曳**NOERROR**如果不是。  
  
### <a name="remarks"></a>備註  
 覆寫此函式可提供回饋給使用者若是置放在此時，會發生什麼情況。 預設實作會使用 OLE 的預設資料指標。 如需有關拖放作業使用 OLE，請參閱文章[拖放 (OLE)](../../mfc/drag-and-drop-ole.md)。  
  
 如需詳細資訊，請參閱[IDropSource::GiveFeedback](http://msdn.microsoft.com/library/windows/desktop/ms693723)， [IDropTarget::DragOver](http://msdn.microsoft.com/library/windows/desktop/ms680129)，和[IDropTarget::DragEnter](http://msdn.microsoft.com/library/windows/desktop/ms680106)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="onbegindrag"></a>COleDropSource::OnBeginDrag  
 由呼叫 framework 發生事件時，就可以開始拖曳作業，例如按下滑鼠左鍵。  
  
```  
virtual BOOL OnBeginDrag(CWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 `pWnd`  
 指向視窗，其中包含所選取的資料。  
  
### <a name="return-value"></a>傳回值  
 如果拖曳允許，否則為 0，非零值。  
  
### <a name="remarks"></a>備註  
 如果您想要修改拖曳的處理序啟動的方式，請覆寫這個函式。 預設實作會捕捉到滑鼠，並且會保持在拖曳模式，直到使用者按下滑鼠左鍵或向右按鈕或按 esc 鍵，此時它會釋放滑鼠按鈕。  
  
##  <a name="querycontinuedrag"></a>COleDropSource::QueryContinueDrag  
 拖曳開始之後，此函式會重複呼叫 framework 直到拖曳作業取消或完成。  
  
```  
virtual SCODE QueryContinueDrag(
    BOOL bEscapePressed, 
    DWORD dwKeyState);
```  
  
### <a name="parameters"></a>參數  
 *bEscapePressed*  
 指出是否已按下 ESC 鍵下自上次呼叫`COleDropSource::QueryContinueDrag`。  
  
 `dwKeyState`  
 包含在鍵盤上的輔助按鍵的狀態。 這是下列任何數目的組合︰ **MK_CONTROL**， **MK_SHIFT**， **MK_ALT**， **MK_LBUTTON**， **MK_MBUTTON**，和**MK_RBUTTON**。  
  
### <a name="return-value"></a>傳回值  
 **DRAGDROP_S_CANCEL**如果按下 ESC 鍵或向右按鈕時，或拖曳啟動之前產生左的按鈕。 **DRAGDROP_S_DROP**如果應該進行拖放作業。 否則`S_OK`。  
  
### <a name="remarks"></a>備註  
 取消此函式如果您想要變更在拖曳點的覆寫或卸除時發生。  
  
 預設實作啟始拖放或取消拖曳，如下所示。 按下 ESC 鍵或滑鼠按鈕時，就會取消拖曳作業。 滑鼠左鍵開始拖曳後引發時，會起始拖放作業。 否則，它會傳回`S_OK`並執行任何進一步的作業。  
  
 此函式會經常被呼叫，因為它應該最佳化儘可能。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 HIERSVR](../../visual-cpp-samples.md)   
 [MFC 範例 OCLIENT](../../visual-cpp-samples.md)   
 [CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)




