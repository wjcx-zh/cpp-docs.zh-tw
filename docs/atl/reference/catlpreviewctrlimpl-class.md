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
caps.latest.revision: 26
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
ms.openlocfilehash: 979dc23eabc2ba2362f7301fc34ca89016d58f37
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="catlpreviewctrlimpl-class"></a>CAtlPreviewCtrlImpl 類別
這個類別是 ATL 實作放置在 Shell for Rich Preview 提供之主機視窗上的視窗。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CAtlPreviewCtrlImpl : public CWindowImpl<CAtlPreviewCtrlImpl>, public IPreviewCtrl;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CAtlPreviewCtrlImpl:: ~ CAtlPreviewCtrlImpl](#dtor)|Destructs 預覽控制項物件。|  
|[CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl](#catlpreviewctrlimpl)|建構預覽控制項物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlPreviewCtrlImpl::Create](#create)|若要建立 Windows 視窗的豐富預覽處理常式呼叫。|  
|[CAtlPreviewCtrlImpl::Destroy](#destroy)|要終結這個控制項需要時，由豐富的預覽處理常式呼叫。|  
|[CAtlPreviewCtrlImpl::Focus](#focus)|設定輸入這個控制項焦點。|  
|[CAtlPreviewCtrlImpl::OnPaint](#onpaint)|處理 WM_PAINT 訊息。|  
|[CAtlPreviewCtrlImpl::Redraw](#redraw)|說明此控制項重繪。|  
|[CAtlPreviewCtrlImpl::SetHost](#sethost)|設定新的父項對這個控制項。|  
|[CAtlPreviewCtrlImpl::SetPreviewVisuals](#setpreviewvisuals)|豐富的預覽處理常式時呼叫必須設定視覺效果豐富的預覽的內容。|  
|[CAtlPreviewCtrlImpl::SetRect](#setrect)|設定這個控制項的新周框矩形。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlPreviewCtrlImpl::DoPaint](#dopaint)|呈現預覽架構呼叫。|  
  
### <a name="protected-constants"></a>受保護的常數  
  
|名稱|說明|  
|----------|-----------------|  
|[CAtlPreviewCtrlImpl::m_plf](#m_plf)|用來在預覽視窗中顯示文字的字型。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlPreviewCtrlImpl::m_clrBack](#m_clrback)|預覽視窗的背景色彩。|  
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
 **標頭︰** atlpreviewctrlimpl.h  
  
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
 提供在 shell for Rich Preview 主應用程式視窗的控制代碼。  
  
 `prc`  
 指定的初始大小和視窗的位置。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為 `TRUE`，否則為 `FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="destroy"></a>CAtlPreviewCtrlImpl::Destroy  
 要終結這個控制項需要時，由豐富的預覽處理常式呼叫。  
  
```
virtual void Destroy();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="dopaint"></a>CAtlPreviewCtrlImpl::DoPaint  
 呈現預覽架構呼叫。  
  
```
virtual void DoPaint(HDC hdc);
```  
  
### <a name="parameters"></a>參數  
 `hdc`  
 若要繪製的裝置內容控制代碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="focus"></a>CAtlPreviewCtrlImpl::Focus  
 設定輸入這個控制項焦點。  
  
```
virtual void Focus();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="m_clrback"></a>CAtlPreviewCtrlImpl::m_clrBack  
 預覽視窗的背景色彩。  
  
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
 說明此控制項重繪。  
  
```
virtual void Redraw();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="sethost"></a>CAtlPreviewCtrlImpl::SetHost  
 設定新的父項對這個控制項。  
  
```
virtual void SetHost(HWND hWndParent);
```  
  
### <a name="parameters"></a>參數  
 `hWndParent`  
 新的父視窗控制代碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setpreviewvisuals"></a>CAtlPreviewCtrlImpl::SetPreviewVisuals  
 豐富的預覽處理常式時呼叫必須設定視覺效果豐富的預覽的內容。  
  
```
virtual void SetPreviewVisuals(
    COLORREF clrBack,
    COLORREF clrText,
    const LOGFONTW* plf);
```  
  
### <a name="parameters"></a>參數  
 `clrBack`  
 預覽視窗的背景色彩。  
  
 `clrText`  
 預覽視窗的文字色彩。  
  
 `plf`  
 用來在預覽視窗中顯示文字的字型。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setrect"></a>CAtlPreviewCtrlImpl::SetRect  
 設定這個控制項的新周框矩形。  
  
```
virtual void SetRect(const RECT* prc, BOOL bRedraw);
```  
  
### <a name="parameters"></a>參數  
 `prc`  
 指定新的大小和預覽控制項的位置。  
  
 `bRedraw`  
 指定是否應該重新繪製控制項。  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [ATL COM 桌面元件](../../atl/atl-com-desktop-components.md)

