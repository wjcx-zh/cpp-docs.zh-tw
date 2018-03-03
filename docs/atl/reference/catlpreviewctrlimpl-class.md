---
title: "CAtlPreviewCtrlImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlPreviewCtrlImpl
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Create
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Destroy
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Focus
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::OnPaint
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Redraw
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::SetHost
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::SetPreviewVisuals
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::SetRect
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::DoPaint
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::m_plf
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::m_clrBack
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::m_clrText
dev_langs:
- C++
helpviewer_keywords:
- CAtlPreviewCtrlImpl class
ms.assetid: 39b3299e-07e4-4abc-9b6e-b54bfa3b0802
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 01c6ac22ecdbf6f66afcec3816ae9d3a3d686942
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="catlpreviewctrlimpl-class"></a>CAtlPreviewCtrlImpl 類別
這個類別是視窗的 ATL 的實作會放在 Shell for Rich Preview 提供主控視窗。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CAtlPreviewCtrlImpl : public CWindowImpl<CAtlPreviewCtrlImpl>, public IPreviewCtrl;
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlPreviewCtrlImpl:: ~ CAtlPreviewCtrlImpl](#dtor)|Destructs 預覽控制項物件。|  
|[CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl](#catlpreviewctrlimpl)|建構預覽控制項物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlPreviewCtrlImpl::Create](#create)|若要建立 Windows 視窗的豐富預覽處理常式呼叫。|  
|[CAtlPreviewCtrlImpl::Destroy](#destroy)|需要終結此控制項時呼叫的豐富預覽處理常式。|  
|[CAtlPreviewCtrlImpl::Focus](#focus)|設定輸入這個控制項的焦點。|  
|[CAtlPreviewCtrlImpl::OnPaint](#onpaint)|處理 WM_PAINT 訊息。|  
|[CAtlPreviewCtrlImpl::Redraw](#redraw)|會告知此控制項重繪。|  
|[CAtlPreviewCtrlImpl::SetHost](#sethost)|設定對這個控制項的新父系。|  
|[CAtlPreviewCtrlImpl::SetPreviewVisuals](#setpreviewvisuals)|由呼叫的豐富預覽處理常式需要設定豐富的預覽的視覺效果時內容。|  
|[CAtlPreviewCtrlImpl::SetRect](#setrect)|設定這個控制項的新週框矩形。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlPreviewCtrlImpl::DoPaint](#dopaint)|由架構呼叫以呈現預覽。|  
  
### <a name="protected-constants"></a>受保護的常數  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlPreviewCtrlImpl::m_plf](#m_plf)|用來在預覽視窗中顯示文字的字型。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlPreviewCtrlImpl::m_clrBack](#m_clrback)|[預覽] 視窗的背景色彩。|  
|[CAtlPreviewCtrlImpl::m_clrText](#m_clrtext)|預覽視窗的文字色彩。|  

  
## <a name="remarks"></a>備註  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `TBase`  
  
 `ATL::CMessageMap`  
  
 `ATL::CWindowImplRoot<TBase>`  
  
 `ATL::CWindowImplBaseT<TBase,TWinTraits>`  
  
 [ATL::CWindowImpl\<CAtlPreviewCtrlImpl >](../../atl/reference/cwindowimpl-class.md)  
  
 `IPreviewCtrl`  
  
 `ATL::CAtlPreviewCtrlImpl`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlpreviewctrlimpl.h  
  
##  <a name="catlpreviewctrlimpl"></a>CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl  
 建構預覽控制項物件。  
  
```
CAtlPreviewCtrlImpl(void) : m_clrText(0),
   m_clrBack(RGB(255, 255, 255)), m_plf(NULL);
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="dtor"></a>CAtlPreviewCtrlImpl:: ~ CAtlPreviewCtrlImpl  
 Destructs 預覽控制項物件。  
  
```
virtual ~CAtlPreviewCtrlImpl(void);
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="create"></a>CAtlPreviewCtrlImpl::Create  
 若要建立 Windows 視窗的豐富預覽處理常式呼叫。  
  
```
virtual BOOL Create(HWND hWndParent, const RECT* prc);
```  
  
### <a name="parameters"></a>參數  
 `hWndParent`  
 在 Shell for Rich Preview 提供主控視窗控制代碼。  
  
 `prc`  
 指定的初始大小和視窗的位置。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為 `TRUE`，否則為 `FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="destroy"></a>CAtlPreviewCtrlImpl::Destroy  
 需要終結此控制項時呼叫的豐富預覽處理常式。  
  
```
virtual void Destroy();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="dopaint"></a>CAtlPreviewCtrlImpl::DoPaint  
 由架構呼叫以呈現預覽。  
  
```
virtual void DoPaint(HDC hdc);
```  
  
### <a name="parameters"></a>參數  
 `hdc`  
 繪製的裝置內容控制代碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="focus"></a>CAtlPreviewCtrlImpl::Focus  
 設定輸入這個控制項的焦點。  
  
```
virtual void Focus();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="m_clrback"></a>CAtlPreviewCtrlImpl::m_clrBack  
 [預覽] 視窗的背景色彩。  
  
```
COLORREF m_clrBack;
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="m_clrtext"></a>CAtlPreviewCtrlImpl::m_clrText  
 預覽視窗的文字色彩。  
  
```
COLORREF m_clrText;
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="m_plf"></a>CAtlPreviewCtrlImpl::m_plf  
 用來在預覽視窗中顯示文字的字型。  
  
```
const LOGFONTW* m_plf;
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="onpaint"></a>CAtlPreviewCtrlImpl::OnPaint  
 處理 WM_PAINT 訊息。  
  
```
LRESULT OnPaint(  
    UINT nMsg,
    WPARAM wParam,
    LPARAM lParam,
    BOOL& bHandled);
```  
  
### <a name="parameters"></a>參數  
 `nMsg`  
 設定為 WM_PAINT。  
  
 `wParam`  
 不使用這個參數。  
  
 `lParam`  
 不使用這個參數。  
  
 `bHandled`  
 此函式傳回時，它包含`TRUE`。  
  
### <a name="return-value"></a>傳回值  
 一律傳回 0。  
  
### <a name="remarks"></a>備註  
  
##  <a name="redraw"></a>CAtlPreviewCtrlImpl::Redraw  
 會告知此控制項重繪。  
  
```
virtual void Redraw();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="sethost"></a>CAtlPreviewCtrlImpl::SetHost  
 設定對這個控制項的新父系。  
  
```
virtual void SetHost(HWND hWndParent);
```  
  
### <a name="parameters"></a>參數  
 `hWndParent`  
 新的父視窗控制代碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setpreviewvisuals"></a>CAtlPreviewCtrlImpl::SetPreviewVisuals  
 由呼叫的豐富預覽處理常式需要設定豐富的預覽的視覺效果時內容。  
  
```
virtual void SetPreviewVisuals(
    COLORREF clrBack,
    COLORREF clrText,
    const LOGFONTW* plf);
```  
  
### <a name="parameters"></a>參數  
 `clrBack`  
 [預覽] 視窗的背景色彩。  
  
 `clrText`  
 預覽視窗的文字色彩。  
  
 `plf`  
 用來在預覽視窗中顯示文字的字型。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setrect"></a>CAtlPreviewCtrlImpl::SetRect  
 設定這個控制項的新週框矩形。  
  
```
virtual void SetRect(const RECT* prc, BOOL bRedraw);
```  
  
### <a name="parameters"></a>參數  
 `prc`  
 指定新的大小和預覽控制項的位置。  
  
 `bRedraw`  
 指定是否應該重繪控制項。  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>請參閱  
 [ATL COM 桌面元件](../../atl/atl-com-desktop-components.md)
