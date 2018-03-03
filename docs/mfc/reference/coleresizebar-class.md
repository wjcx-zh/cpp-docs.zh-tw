---
title: "COleResizeBar 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleResizeBar
- AFXOLE/COleResizeBar
- AFXOLE/COleResizeBar::COleResizeBar
- AFXOLE/COleResizeBar::Create
dev_langs:
- C++
helpviewer_keywords:
- COleResizeBar [MFC], COleResizeBar
- COleResizeBar [MFC], Create
ms.assetid: 56a708d9-28c5-4eb0-9404-77b688d91c63
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0cc0b9f85392a69191ee3c948985c61bd2d1f494
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="coleresizebar-class"></a>COleResizeBar 類別
支援就地 OLE 項目調整大小的控制列類型。  
  
## <a name="syntax"></a>語法  
  
```  
class COleResizeBar : public CControlBar  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[COleResizeBar::COleResizeBar](#coleresizebar)|建構 `COleResizeBar` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[COleResizeBar::Create](#create)|建立和初始化 Windows 子視窗，並產生關聯來`COleResizeBar`物件。|  
  
## <a name="remarks"></a>備註  
 `COleResizeBar`物件會顯示為[CRectTracker](../../mfc/reference/crecttracker-class.md)具有陰影的框線和外部調整大小控點。  
  
 `COleResizeBar`物件是衍生自的框架視窗物件通常是內嵌的成員[COleIPFrameWnd](../../mfc/reference/coleipframewnd-class.md)類別。  
  
 如需詳細資訊，請參閱文章[啟用](../../mfc/activation-cpp.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `COleResizeBar`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxole.h  
  
##  <a name="coleresizebar"></a>COleResizeBar::COleResizeBar  
 建構 `COleResizeBar` 物件。  
  
```  
COleResizeBar();
```  
  
### <a name="remarks"></a>備註  
 呼叫**建立**建立調整列物件。  
  
##  <a name="create"></a>COleResizeBar::Create  
 建立子視窗，並將其與相關聯`COleResizeBar`物件。  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE,  
    UINT nID = AFX_IDW_RESIZE_BAR);
```  
  
### <a name="parameters"></a>參數  
 `pParentWnd`  
 父視窗的大小調整列的指標。  
  
 `dwStyle`  
 指定[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)屬性。  
  
 `nID`  
 大小調整列的子視窗識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果已建立的大小調整列; 非零，否則便是 0。  
  
## <a name="see-also"></a>請參閱  
 [MFC 範例 SUPERPAD](../../visual-cpp-samples.md)   
 [CControlBar 類別](../../mfc/reference/ccontrolbar-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleServerDoc 類別](../../mfc/reference/coleserverdoc-class.md)
