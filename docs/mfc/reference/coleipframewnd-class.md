---
title: "COleIPFrameWnd 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleIPFrameWnd
dev_langs:
- C++
helpviewer_keywords:
- COleIPFrameWnd class
- OLE, editing
- OLE, in-place activation
- in-place editing
ms.assetid: 24abb2cb-826c-4dda-a287-d8a8900a5763
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
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 85ce028bb5d72c06a0e228abba1bd08a7f6526cb
ms.lasthandoff: 02/24/2017

---
# <a name="coleipframewnd-class"></a>COleIPFrameWnd 類別
應用程式就地編輯視窗的基底。  
  
## <a name="syntax"></a>語法  
  
```  
class COleIPFrameWnd : public CFrameWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[COleIPFrameWnd::COleIPFrameWnd](#coleipframewnd)|建構 `COleIPFrameWnd` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[COleIPFrameWnd::OnCreateControlBars](#oncreatecontrolbars)|進行就地編輯項目啟動時，由架構呼叫。|  
|[COleIPFrameWnd::RepositionFrame](#repositionframe)|若要重新定位在就地編輯視窗架構呼叫。|  
  
## <a name="remarks"></a>備註  
 這個類別會建立並位置控制容器應用程式的文件視窗內的橫條圖。 它也會處理產生內嵌通知[Coleipframewnd](../../mfc/reference/coleresizebar-class.md)物件當使用者調整就地編輯視窗。  
  
 如需有關使用`COleIPFrameWnd`，請參閱文章[啟用](../../mfc/activation-cpp.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 `COleIPFrameWnd`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxole.h  
  
##  <a name="a-namecoleipframewnda--coleipframewndcoleipframewnd"></a><a name="coleipframewnd"></a>COleIPFrameWnd::COleIPFrameWnd  
 建構`COleIPFrameWnd`物件，並初始化其就地狀態資訊，儲存在型別的結構**OLEINPLACEFRAMEINFO**。  
  
```  
COleIPFrameWnd();
```  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[OLEINPLACEFRAMEINFO](http://msdn.microsoft.com/library/windows/desktop/ms693737)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameoncreatecontrolbarsa--coleipframewndoncreatecontrolbars"></a><a name="oncreatecontrolbars"></a>COleIPFrameWnd::OnCreateControlBars  
 這個架構會呼叫`OnCreateControlBars`函式時的就地編輯啟動項目。  
  
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
 如果成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 預設實作不做任何動作。 覆寫這個函式來執行時所建立的控制列所需的任何特殊處理。  
  
##  <a name="a-namerepositionframea--coleipframewndrepositionframe"></a><a name="repositionframe"></a>COleIPFrameWnd::RepositionFrame  
 這個架構會呼叫`RepositionFrame`配置控制列，並重新定位在就地編輯視窗，讓全部都是可見的成員函式。  
  
```  
virtual void RepositionFrame(
    LPCRECT lpPosRect,  
    LPCRECT lpClipRect);
```  
  
### <a name="parameters"></a>參數  
 `lpPosRect`  
 指標`RECT`結構或`CRect`物件，其中包含就地框架視窗的目前位置座標，像素為單位，相對於用戶端區域。  
  
 `lpClipRect`  
 指標`RECT`結構或`CRect`物件，其中包含就地框架視窗的目前裁剪矩形座標，像素為單位，相對於用戶端區域。  
  
### <a name="remarks"></a>備註  
 在 [容器] 視窗的控制列的配置與&1;-up 執行的非 OLE 框架視窗。 在非 OLE 框架視窗計算的控制列和其他物件，從指定的框架視窗大小，如下所示的呼叫位置[CFrameWnd::RecalcLayout](../../mfc/reference/cframewnd-class.md#recalclayout)。 工作區是減去的控制列和其他物件的空間之後，還會保留。 A `COleIPFrameWnd`  視窗中，相反地，將工具列根據給定的用戶端區域。 換句話說，`CFrameWnd::RecalcLayout`適用 「 從外部，「 `COleIPFrameWnd::RepositionFrame` 」 由內而外。 」 的運作方式  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 HIERSVR](../../visual-cpp-samples.md)   
 [CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)

