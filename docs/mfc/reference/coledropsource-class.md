---
title: COleDropSource 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- COleDropSource [MFC], COleDropSource
- COleDropSource [MFC], GiveFeedback
- COleDropSource [MFC], OnBeginDrag
- COleDropSource [MFC], QueryContinueDrag
ms.assetid: d3eecc5f-a70b-4a01-b705-7d2c098ebe17
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 41e79ac918c1a549c7972d5feccf4f470473f98c
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/05/2018
ms.locfileid: "37852911"
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
|[COleDropSource::GiveFeedback](#givefeedback)|拖放作業期間變更的資料指標。|  
|[COleDropSource::OnBeginDrag](#onbegindrag)|拖放作業期間，會處理滑鼠捕捉。|  
|[COleDropSource::QueryContinueDrag](#querycontinuedrag)|檢查拖曳是否應該繼續執行。|  
  
## <a name="remarks"></a>備註  
 [COleDropTarget](../../mfc/reference/coledroptarget-class.md)類別處理拖放作業的接收部分。 `COleDropSource`物件負責判斷在拖曳作業開始時、 提供意見反應拖曳作業期間，以及決定結束拖曳作業。  
  
 若要使用`COleDropSource`物件，只會呼叫建構函式。 這可簡化程序可決定哪些事件，例如按下滑鼠，可讓您開始拖曳作業，使用[coledatasource:: Dodragdrop](../../mfc/reference/coledatasource-class.md#dodragdrop)， [COleClientItem::DoDragDrop](../../mfc/reference/coleclientitem-class.md#dodragdrop)，或[COleServerItem::DoDragDrop](../../mfc/reference/coleserveritem-class.md#dodragdrop)函式。 這些函式會建立`COleDropSource`為您的物件。 您可能想要修改的預設行為`COleDropSource`可覆寫的函式。 由架構，這些成員函式會在適當的時間呼叫。  
  
 如需有關拖放作業使用 OLE，請參閱文章[拖放 (OLE)](../../mfc/drag-and-drop-ole.md)。  
  
 如需詳細資訊，請參閱 < [IDropSource](http://msdn.microsoft.com/library/windows/desktop/ms690071) Windows SDK 中。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleDropSource`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxole.h  
  
##  <a name="coledropsource"></a>  COleDropSource::COleDropSource  
 建構 `COleDropSource` 物件。  
  
```  
COleDropSource();
```  
  
##  <a name="givefeedback"></a>  COleDropSource::GiveFeedback  
 由架構呼叫之後呼叫[COleDropTarget::OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover)或是[COleDropTarget::DragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter)。  
  
```  
virtual SCODE GiveFeedback(DROPEFFECT dropEffect);
```  
  
### <a name="parameters"></a>參數  
 *dropEffect*  
 若是置放在此點與所選取的資料，您想要向使用者顯示的效果，通常表示項目會發生。 一般而言，這是最新的呼叫所傳回的值[CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter)或是[CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover)。 它可以是下列其中一個或多個項目：  
  
- DROPEFFECT_NONE 不會允許卸除。  
  
- DROPEFFECT_COPY 執行複製作業。  
  
- DROPEFFECT_MOVE 會執行移動作業。  
  
- 會建立已卸除的資料從原始資料的 DROPEFFECT_LINK 的連結。  
  
- DROPEFFECT_SCROLL A 拖曳捲軸作業會發生，或在目標中進行。  
  
### <a name="return-value"></a>傳回值  
 傳回 DRAGDROP_S_USEDEFAULTCURSORS 拖曳如果正在進行中，如果不是 NOERROR。  
  
### <a name="remarks"></a>備註  
 覆寫此函式以提供若是置放在此時，會發生什麼情況的相關使用者的意見反應。 預設實作會使用 OLE 的預設資料指標。 如需有關拖放作業使用 OLE，請參閱文章[拖放 (OLE)](../../mfc/drag-and-drop-ole.md)。  
  
 如需詳細資訊，請參閱 < [IDropSource::GiveFeedback](http://msdn.microsoft.com/library/windows/desktop/ms693723)， [IDropTarget::DragOver](http://msdn.microsoft.com/library/windows/desktop/ms680129)，並[IDropTarget::DragEnter](http://msdn.microsoft.com/library/windows/desktop/ms680106) Windows SDK 中。  
  
##  <a name="onbegindrag"></a>  COleDropSource::OnBeginDrag  
 呼叫 framework 發生事件時，無法開始拖曳作業，例如按下滑鼠左的按鈕。  
  
```  
virtual BOOL OnBeginDrag(CWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 *pWnd*  
 指向視窗，其中包含所選取的資料。  
  
### <a name="return-value"></a>傳回值  
 如果拖曳允許，否則為 0，非零值。  
  
### <a name="remarks"></a>備註  
 如果您想要修改拖曳的處理序啟動的方式，請覆寫這個函式。 預設實作會擷取滑鼠，並會保持在拖曳模式，直到使用者按下滑鼠左鍵或右鍵按鈕或按 esc 鍵，此時它會釋放滑鼠按鈕。  
  
##  <a name="querycontinuedrag"></a>  COleDropSource::QueryContinueDrag  
 拖曳開始之後，此函式會重複呼叫 framework 直到取消或完成拖曳作業為止。  
  
```  
virtual SCODE QueryContinueDrag(
    BOOL bEscapePressed, 
    DWORD dwKeyState);
```  
  
### <a name="parameters"></a>參數  
 *bEscapePressed*  
 指出是否有已按下 ESC 鍵自上次呼叫`COleDropSource::QueryContinueDrag`。  
  
 *dwKeyState*  
 包含在鍵盤上的輔助按鍵的狀態。 這是任意數目的下列組合： MK_CONTROL、 MK_SHIFT、 MK_ALT、 MK_LBUTTON、 MK_MBUTTON 和 MK_RBUTTON。  
  
### <a name="return-value"></a>傳回值  
 DRAGDROP_S_CANCEL 如果 ESC 鍵或向右按鈕已按下，還是保留按鈕就會引發之前拖曳開始。 如果應該卸除作業，DRAGDROP_S_DROP。 否則為 S_OK。  
  
### <a name="remarks"></a>備註  
 取消此函式如果您想要變更之起點的拖曳的覆寫或 drop 時發生。  
  
 預設實作會起始拖放，或取消拖曳，如下所示。 按下 ESC 鍵或滑鼠按鈕時，它就會取消拖曳作業。 拖曳啟動之後，就會引發滑鼠左鍵時，它就會起始拖放作業。 否則，它會傳回 s_ok 時，會執行任何進一步的作業。  
  
 因為經常呼叫此函式，它應該最佳化盡量。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 HIERSVR](../../visual-cpp-samples.md)   
 [MFC 範例 OCLIENT](../../visual-cpp-samples.md)   
 [CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)



