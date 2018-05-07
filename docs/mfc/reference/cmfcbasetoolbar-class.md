---
title: CMFCBaseToolBar 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCBaseToolBar
- AFXBASETOOLBAR/CMFCBaseToolBar
- AFXBASETOOLBAR/CMFCBaseToolBar::GetDockingMode
- AFXBASETOOLBAR/CMFCBaseToolBar::GetMinSize
- AFXBASETOOLBAR/CMFCBaseToolBar::OnAfterChangeParent
dev_langs:
- C++
helpviewer_keywords:
- CMFCBaseToolBar [MFC], GetDockingMode
- CMFCBaseToolBar [MFC], GetMinSize
- CMFCBaseToolBar [MFC], OnAfterChangeParent
ms.assetid: 5d79206d-55e4-46f8-b1b8-042e34d7f9da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: edc35091fef87c007fad73be45297536a170ca19
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcbasetoolbar-class"></a>CMFCBaseToolBar 類別
工具列的基底類別。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCBaseToolBar : public CPane  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|`CMFCBaseToolBar::CMFCBaseToolBar`|預設建構函式。|  
|`CMFCBaseToolBar::~CMFCBaseToolBar`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|`CMFCBaseToolBar::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|  
|[CMFCBaseToolBar::GetDockingMode](#getdockingmode)|傳回固定模式。 (覆寫[cbasepane:: Getdockingmode](../../mfc/reference/cbasepane-class.md#getdockingmode)。)|  
|[CMFCBaseToolBar::GetMinSize](#getminsize)|傳回的最小的工具列。 (覆寫[CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize)。)|  
|[CMFCBaseToolBar::OnAfterChangeParent](#onafterchangeparent)|窗格的父代變更之後，由架構呼叫。 (覆寫[CBasePane::OnAfterChangeParent](../../mfc/reference/cbasepane-class.md#onafterchangeparent)。)|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxbasetoolbar.h  
  
##  <a name="getdockingmode"></a>  CMFCBaseToolBar::GetDockingMode  
 傳回固定模式。  
  
```  
virtual AFX_DOCK_TYPE GetDockingMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 停駐的模式。  
  
##  <a name="getminsize"></a>  CMFCBaseToolBar::GetMinSize  
 傳回的最小的工具列。  
  
```  
virtual void GetMinSize(CSize& size) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `size`  
 工具列的大小下限。  
  
##  <a name="onafterchangeparent"></a>  CMFCBaseToolBar::OnAfterChangeParent  
 窗格的父代變更之後，由架構呼叫。  
  
```  
virtual void OnAfterChangeParent(CWnd* pWndOldParent);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pWndOldParent`  
 先前的父視窗的指標。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)
