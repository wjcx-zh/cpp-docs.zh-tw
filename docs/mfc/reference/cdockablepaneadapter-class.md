---
title: CDockablePaneAdapter 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDockablePaneAdapter
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::GetWrappedWnd
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::LoadState
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::SaveState
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::SetWrappedWnd
dev_langs:
- C++
helpviewer_keywords:
- CDockablePaneAdapter [MFC], GetWrappedWnd
- CDockablePaneAdapter [MFC], LoadState
- CDockablePaneAdapter [MFC], SaveState
- CDockablePaneAdapter [MFC], SetWrappedWnd
ms.assetid: 6ed6cf82-f39c-4d0c-bf7c-8641495cf8f3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 71d89020869db10b45688dbaae71f38711d2667c
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43676359"
---
# <a name="cdockablepaneadapter-class"></a>CDockablePaneAdapter 類別
提供 `CWnd`衍生窗格的停駐支援。  
  
## <a name="syntax"></a>語法  
  
```  
class CDockablePaneAdapter : public CDockablePane  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CDockablePaneAdapter::GetWrappedWnd](#getwrappedwnd)|傳回已包裝的視窗。|  
|[CDockablePaneAdapter::LoadState](#loadstate)|(覆寫[cdockablepane:: Loadstate](cdockablepane-class.md#loadstate)。)|  
|[CDockablePaneAdapter::SaveState](#savestate)|(覆寫[cdockablepane:: Savestate](cdockablepane-class.md)。)|  
|[CDockablePaneAdapter::SetWrappedWnd](#setwrappedwnd)||  
  
## <a name="remarks"></a>備註  
 通常，架構會具現化這個類別的物件使用時[:: Addtab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab)或是[cmfcbasetabctrl:: Inserttab](../../mfc/reference/cmfcbasetabctrl-class.md#inserttab)方法。  
  
 如果您想要自訂`CDockablePaneAdapter`行為，只要從中衍生新類別，並使用將執行階段類別資訊設為索引標籤式視窗[:: Setdockingbarwrapperrtc](../../mfc/reference/cmfcbasetabctrl-class.md#setdockingbarwrapperrtc)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md) [CPane](../../mfc/reference/cpane-class.md) [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxDockablePaneAdapter.h  
  
##  <a name="getwrappedwnd"></a>  CDockablePaneAdapter::GetWrappedWnd  
 傳回可停駐窗格配接器的基礎視窗。  
  
```  
virtual CWnd* GetWrappedWnd() const;  
```  
  
### <a name="return-value"></a>傳回值  
 已包裝的視窗指標。  
  
### <a name="remarks"></a>備註  
 您可以使用此函式來存取已包裝的視窗。  
  
##  <a name="loadstate"></a>  CDockablePaneAdapter::LoadState  
 從登錄載入窗格的狀態。  
  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    int nIndex = -1,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>參數  
 [in]*lpszProfileName*  
 設定檔名稱。  
  
 [in]*nIndex*  
 設定檔的索引。  
  
 [in]*uiID*  
 窗格中的識別碼。  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="savestate"></a>  CDockablePaneAdapter::SaveState  
 將窗格的狀態儲存至登錄中。  
  
```  
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,  
    int nIndex = -1,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>參數  
 [in]*lpszProfileName*  
 設定檔名稱。  
  
 [in]*nIndex*  
 設定檔的索引 （預設為視窗的控制項 ID）。  
  
 [in]*uiID*  
 窗格中的識別碼。  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="setwrappedwnd"></a>  CDockablePaneAdapter::SetWrappedWnd  
 設定可停駐窗格配接器的基礎視窗。  
  
```  
virtual BOOL SetWrappedWnd(CWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 [in]*pWnd*  
 視窗窗格配接器要包裝的指標。  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)
