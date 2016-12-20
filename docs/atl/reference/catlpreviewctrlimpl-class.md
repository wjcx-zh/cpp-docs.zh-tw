---
title: "CAtlPreviewCtrlImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "atlpreviewctrlimpl/ATL::CAtlPreviewCtrlImpl"
  - "CAtlPreviewCtrlImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlPreviewCtrlImpl class"
ms.assetid: 39b3299e-07e4-4abc-9b6e-b54bfa3b0802
caps.latest.revision: 26
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAtlPreviewCtrlImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別是在 Shell 所提供的裝載視窗上提供豐富預覽視窗的 ATL 實作。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
class CAtlPreviewCtrlImpl : public CWindowImpl<CAtlPreviewCtrlImpl>, public IPreviewCtrl;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CAtlPreviewCtrlImpl::~CAtlPreviewCtrlImpl](../Topic/CAtlPreviewCtrlImpl::~CAtlPreviewCtrlImpl.md)|解構預覽控制項物件。|  
|[CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl](../Topic/CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl.md)|建構預覽控制項物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CAtlPreviewCtrlImpl::Create](../Topic/CAtlPreviewCtrlImpl::Create.md)|呼叫了豐富的預覽處理常式建立視窗的視窗。|  
|[CAtlPreviewCtrlImpl::Destroy](../Topic/CAtlPreviewCtrlImpl::Destroy.md)|呼叫了豐富的預覽處理常式，在需要終結此控制項。|  
|[CAtlPreviewCtrlImpl::Focus](../Topic/CAtlPreviewCtrlImpl::Focus.md)|對這個控制項設定輸入焦點。|  
|[CAtlPreviewCtrlImpl::OnPaint](../Topic/CAtlPreviewCtrlImpl::OnPaint.md)|處理 WM\_PAINT 訊息。|  
|[CAtlPreviewCtrlImpl::Redraw](../Topic/CAtlPreviewCtrlImpl::Redraw.md)|呼叫這個控制項重繪。|  
|[CAtlPreviewCtrlImpl::SetHost](../Topic/CAtlPreviewCtrlImpl::SetHost.md)|設定這個控制項的新父代。|  
|[CAtlPreviewCtrlImpl::SetPreviewVisuals](../Topic/CAtlPreviewCtrlImpl::SetPreviewVisuals.md)|呼叫了豐富的預覽處理常式，在需要將豐富預覽內容之視覺化。|  
|[CAtlPreviewCtrlImpl::SetRect](../Topic/CAtlPreviewCtrlImpl::SetRect.md)|將這個控制項建立新的週框 \(Bounding Rectangle\)。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CAtlPreviewCtrlImpl::DoPaint](../Topic/CAtlPreviewCtrlImpl::DoPaint.md)|呼叫由架構所呈現預覽。|  
  
### 受保護的常數。  
  
|名稱|描述|  
|--------|--------|  
|[CAtlPreviewCtrlImpl::m\_plf](../Topic/CAtlPreviewCtrlImpl::m_plf.md)|字型是由顯示在預覽視窗中的文字。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CAtlPreviewCtrlImpl::m\_clrBack](../Topic/CAtlPreviewCtrlImpl::m_clrBack.md)|預覽視窗的背景色彩。|  
|[CAtlPreviewCtrlImpl::m\_clrText](../Topic/CAtlPreviewCtrlImpl::m_clrText.md)|預覽視窗文字色彩。|  
  
## 備註  
  
## 繼承階層架構  
 `TBase`  
  
 `ATL::CMessageMap`  
  
 `ATL::CWindowImplRoot<TBase>`  
  
 `ATL::CWindowImplBaseT<TBase,TWinTraits>`  
  
 [ATL::CWindowImpl\<CAtlPreviewCtrlImpl\>](../../atl/reference/cwindowimpl-class.md)  
  
 `IPreviewCtrl`  
  
 `ATL::CAtlPreviewCtrlImpl`  
  
## 需求  
 **Header:** atlpreviewctrlimpl.h  
  
## 請參閱  
 [ATL COM Desktop Components](../../atl/atl-com-desktop-components.md)