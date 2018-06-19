---
title: COleIPFrameWnd 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleIPFrameWnd
- AFXOLE/COleIPFrameWnd
- AFXOLE/COleIPFrameWnd::COleIPFrameWnd
- AFXOLE/COleIPFrameWnd::OnCreateControlBars
- AFXOLE/COleIPFrameWnd::RepositionFrame
dev_langs:
- C++
helpviewer_keywords:
- COleIPFrameWnd [MFC], COleIPFrameWnd
- COleIPFrameWnd [MFC], OnCreateControlBars
- COleIPFrameWnd [MFC], RepositionFrame
ms.assetid: 24abb2cb-826c-4dda-a287-d8a8900a5763
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 466948653a5464a940a027e473e79c00dbf9a6ab
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370376"
---
# <a name="coleipframewnd-class"></a>COleIPFrameWnd 類別
應用程式就地編輯視窗的基底。  
  
## <a name="syntax"></a>語法  
  
```  
class COleIPFrameWnd : public CFrameWnd  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[COleIPFrameWnd::COleIPFrameWnd](#coleipframewnd)|建構 `COleIPFrameWnd` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[COleIPFrameWnd::OnCreateControlBars](#oncreatecontrolbars)|進行就地編輯啟動項目時由架構呼叫。|  
|[COleIPFrameWnd::RepositionFrame](#repositionframe)|由架構呼叫以重新定位就地編輯視窗。|  
  
## <a name="remarks"></a>備註  
 這個類別會建立並位置控制容器應用程式的文件視窗中的列。 它也會產生內嵌通知處理[COleResizeBar](../../mfc/reference/coleresizebar-class.md)當使用者調整大小時就地編輯視窗的物件。  
  
 如需有關使用`COleIPFrameWnd`，請參閱文章[啟用](../../mfc/activation-cpp.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 `COleIPFrameWnd`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxole.h  
  
##  <a name="coleipframewnd"></a>  COleIPFrameWnd::COleIPFrameWnd  
 建構`COleIPFrameWnd`物件，並初始化其就地狀態資訊，儲存在結構中的型別**OLEINPLACEFRAMEINFO**。  
  
```  
COleIPFrameWnd();
```  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[OLEINPLACEFRAMEINFO](http://msdn.microsoft.com/library/windows/desktop/ms693737) Windows SDK 中。  
  
##  <a name="oncreatecontrolbars"></a>  COleIPFrameWnd::OnCreateControlBars  
 這個架構會呼叫`OnCreateControlBars`函式時就地編輯的啟動項目。  
  
```  
virtual BOOL OnCreateControlBars(
    CWnd* pWndFrame,  
    CWnd* pWndDoc);

 
virtual BOOL OnCreateControlBars(
    CFrameWnd* pWndFrame,  
    CFrameWnd* pWndDoc);
```  
  
### <a name="parameters"></a>參數  
 *pWndFrame*  
 容器應用程式的框架視窗的指標。  
  
 *pWndDoc*  
 容器的文件層級視窗的指標。 可以是**NULL**如果容器是 SDI 應用程式。  
  
### <a name="return-value"></a>傳回值  
 非零成功;否則為 0。  
  
### <a name="remarks"></a>備註  
 預設實作不做任何動作。 覆寫這個函式來執行建立控制列時所需的任何特殊處理。  
  
##  <a name="repositionframe"></a>  COleIPFrameWnd::RepositionFrame  
 這個架構會呼叫`RepositionFrame`配置控制列，並調整就地編輯視窗的位置，所以全部都是可見的成員函式。  
  
```  
virtual void RepositionFrame(
    LPCRECT lpPosRect,  
    LPCRECT lpClipRect);
```  
  
### <a name="parameters"></a>參數  
 `lpPosRect`  
 指標`RECT`結構或`CRect`物件，其中包含的就地框架視窗的目前位置座標，以像素為單位，相對於用戶端區域中。  
  
 `lpClipRect`  
 指標`RECT`結構或`CRect`物件，其中包含的就地框架視窗的目前裁剪方框座標，以像素為單位，相對於用戶端區域中。  
  
### <a name="remarks"></a>備註  
 在容器視窗中的控制列的配置與 1-up 執行的非 OLE 框架視窗。 非 OLE 框架視窗計算控制列和從指定的框架視窗大小，如同要呼叫的其他物件的位置[CFrameWnd::RecalcLayout](../../mfc/reference/cframewnd-class.md#recalclayout)。 工作區是剩下之後減去的控制列和其他物件的空間。 A`COleIPFrameWnd`視窗中，相反地，根據給定的用戶端區域放置工具列。 換句話說，`CFrameWnd::RecalcLayout`運作 」 從，在外部"，而`COleIPFrameWnd::RepositionFrame`會 」 從內而外。 」  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 HIERSVR](../../visual-cpp-samples.md)   
 [CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)
