---
title: "COleDropSource 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleDropSource
- AFXOLE/COleDropSource
- AFXOLE/COleDropSource::COleDropSource
- AFXOLE/COleDropSource::GiveFeedback
- AFXOLE/COleDropSource::OnBeginDrag
- AFXOLE/COleDropSource::QueryContinueDrag
dev_langs: C++
helpviewer_keywords:
- COleDropSource [MFC], COleDropSource
- COleDropSource [MFC], GiveFeedback
- COleDropSource [MFC], OnBeginDrag
- COleDropSource [MFC], QueryContinueDrag
ms.assetid: d3eecc5f-a70b-4a01-b705-7d2c098ebe17
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 486a236075ff33093b9a734d7f368e05ed29588e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="coledropsource-class"></a>COleDropSource 類別
允許將資料拖曳到置放目標。  
  
## <a name="syntax"></a>語法  
  
```  
class COleDropSource : public CCmdTarget  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[COleDropSource::COleDropSource](#coledropsource)|建構 `COleDropSource` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[COleDropSource::GiveFeedback](#givefeedback)|拖放作業期間會變更資料指標。|  
|[COleDropSource::OnBeginDrag](#onbegindrag)|拖放作業期間，會處理滑鼠捕捉。|  
|[COleDropSource::QueryContinueDrag](#querycontinuedrag)|會檢查拖曳是否應該繼續執行。|  
  
## <a name="remarks"></a>備註  
 [COleDropTarget](../../mfc/reference/coledroptarget-class.md)類別處理拖放作業的接收部分。 `COleDropSource`物件負責決定在拖曳作業開始時、 提供意見反應拖曳作業期間，以及決定結束拖曳作業。  
  
 若要使用`COleDropSource`物件，只需要呼叫建構函式。 這樣可簡化決定哪些事件，例如滑鼠點選開始拖曳作業使用的程序[coledatasource:: Dodragdrop](../../mfc/reference/coledatasource-class.md#dodragdrop)， [COleClientItem::DoDragDrop](../../mfc/reference/coleclientitem-class.md#dodragdrop)，或[COleServerItem::DoDragDrop](../../mfc/reference/coleserveritem-class.md#dodragdrop)函式。 這些函式會建立`COleDropSource`為您的物件。 您可能想要修改的預設行為`COleDropSource`可覆寫的函式。 由架構，這些成員函式會在適當時間呼叫。  
  
 如需拖放作業使用 OLE，請參閱文章[拖放 (OLE)](../../mfc/drag-and-drop-ole.md)。  
  
 如需詳細資訊，請參閱[IDropSource](http://msdn.microsoft.com/library/windows/desktop/ms690071) Windows SDK 中。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleDropSource`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxole.h  
  
##  <a name="coledropsource"></a>COleDropSource::COleDropSource  
 建構 `COleDropSource` 物件。  
  
```  
COleDropSource();
```  
  
##  <a name="givefeedback"></a>COleDropSource::GiveFeedback  
 由架構呼叫之後呼叫[COleDropTarget::OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover)或[COleDropTarget::DragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter)。  
  
```  
virtual SCODE GiveFeedback(DROPEFFECT dropEffect);
```  
  
### <a name="parameters"></a>參數  
 `dropEffect`  
 通常指出項目會發生您想要向使用者顯示的效果，則卸除發生了此點與所選取的資料。 一般而言，這是最新的呼叫所傳回的值[CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter)或[CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover)。 它可以是下列一或多個項目：  
  
- `DROPEFFECT_NONE`不允許卸除。  
  
- `DROPEFFECT_COPY`執行複製作業。  
  
- `DROPEFFECT_MOVE`會執行移動作業。  
  
- `DROPEFFECT_LINK`會建立已卸除的資料從原始資料的連結。  
  
- `DROPEFFECT_SCROLL`拖曳捲軸作業即將發生或正在進行中的目標。  
  
### <a name="return-value"></a>傳回值  
 傳回**DRAGDROP_S_USEDEFAULTCURSORS**如果已在進行中，拖曳**NOERROR**如果不是。  
  
### <a name="remarks"></a>備註  
 覆寫此函式可提供意見反應給使用者置放發生此時會發生什麼事。 預設實作會使用 OLE 的預設資料指標。 如需拖放作業使用 OLE，請參閱文章[拖放 (OLE)](../../mfc/drag-and-drop-ole.md)。  
  
 如需詳細資訊，請參閱[IDropSource::GiveFeedback](http://msdn.microsoft.com/library/windows/desktop/ms693723)， [IDropTarget::DragOver](http://msdn.microsoft.com/library/windows/desktop/ms680129)，和[IDropTarget::DragEnter](http://msdn.microsoft.com/library/windows/desktop/ms680106) Windows SDK 中。  
  
##  <a name="onbegindrag"></a>COleDropSource::OnBeginDrag  
 由呼叫發生事件時，framework 就可以開始拖曳作業，例如按下滑鼠左的按鈕。  
  
```  
virtual BOOL OnBeginDrag(CWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 `pWnd`  
 指向視窗，其中包含所選取的資料。  
  
### <a name="return-value"></a>傳回值  
 非零，如果拖曳允許，否則為 0。  
  
### <a name="remarks"></a>備註  
 如果您想要修改拖曳的處理序啟動的方式，請覆寫這個函式。 預設實作會擷取滑鼠，並會保持在拖放到模式，直到使用者按下滑鼠左鍵或右鍵按鈕或按 esc 鍵，此時它會釋放滑鼠按鈕。  
  
##  <a name="querycontinuedrag"></a>COleDropSource::QueryContinueDrag  
 拖曳開始之後，此函式會重複呼叫架構直到取消或完成拖曳作業為止。  
  
```  
virtual SCODE QueryContinueDrag(
    BOOL bEscapePressed, 
    DWORD dwKeyState);
```  
  
### <a name="parameters"></a>參數  
 *bEscapePressed*  
 指出是否已在上次呼叫後按下 ESC 鍵`COleDropSource::QueryContinueDrag`。  
  
 `dwKeyState`  
 包含在鍵盤上的輔助按鍵的狀態。 這是任意數目的下列組合： **MK_CONTROL**， **MK_SHIFT**， **MK_ALT**， **MK_LBUTTON**， **MK_MBUTTON**，和**MK_RBUTTON**。  
  
### <a name="return-value"></a>傳回值  
 **DRAGDROP_S_CANCEL**如果按下 ESC 鍵或向右按鈕時，或拖曳啟動之前引發左邊的按鈕。 **DRAGDROP_S_DROP**是否應該發生拖放作業。 否則`S_OK`。  
  
### <a name="remarks"></a>備註  
 取消此函式如果您想要變更在拖曳點的覆寫或 drop 時發生。  
  
 預設實作啟始拖放或取消拖曳，如下所示。 按下 ESC 鍵或滑鼠按鈕時，它就會取消拖曳作業。 當滑鼠左鍵拖曳啟動之後，就會引發時，會起始卸除作業。 否則，它會傳回`S_OK`並執行任何進一步的作業。  
  
 因為經常呼叫此函式，它應該最佳化盡量。  
  
## <a name="see-also"></a>請參閱  
 [MFC 範例 HIERSVR](../../visual-cpp-samples.md)   
 [MFC 範例 OCLIENT](../../visual-cpp-samples.md)   
 [CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)



