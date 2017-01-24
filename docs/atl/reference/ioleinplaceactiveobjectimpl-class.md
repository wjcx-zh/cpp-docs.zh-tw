---
title: "IOleInPlaceActiveObjectImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IOleInPlaceActiveObjectImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控制項 [C++], communication between container and control"
  - "IOleInPlaceActiveObject, ATL 實作"
  - "IOleInPlaceActiveObjectImpl class"
ms.assetid: 44e6cc6d-a2dc-4187-98e3-73cf0320dea9
caps.latest.revision: 22
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IOleInPlaceActiveObjectImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會提供協助就地控制項與其容器之間通訊的方法。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]執行的應用程式。  
  
## 語法  
  
```  
  
      template< class   
      T  
      >  
class IOleInPlaceActiveObjectImpl  
```  
  
#### 參數  
 `T`  
 您的類別，衍生自 `IOleInPlaceActiveObjectImpl`。  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[IOleInPlaceActiveObjectImpl::ContextSensitiveHelp](../Topic/IOleInPlaceActiveObjectImpl::ContextSensitiveHelp.md)|啟用即時線上說明。  ATL 實作會傳回 **E\_NOTIMPL**。|  
|[IOleInPlaceActiveObjectImpl::EnableModeless](../Topic/IOleInPlaceActiveObjectImpl::EnableModeless.md)|可為非強制回應對話方塊。  ATL 實作會傳回 `S_OK`。|  
|[IOleInPlaceActiveObjectImpl::GetWindow](../Topic/IOleInPlaceActiveObjectImpl::GetWindow.md)|取得視窗控制代碼。|  
|[IOleInPlaceActiveObjectImpl::OnDocWindowActivate](../Topic/IOleInPlaceActiveObjectImpl::OnDocWindowActivate.md)|在容器的文件視窗中啟用或停用時，告知控制項。  ATL 實作會傳回 `S_OK`。|  
|[IOleInPlaceActiveObjectImpl::OnFrameWindowActivate](../Topic/IOleInPlaceActiveObjectImpl::OnFrameWindowActivate.md)|在容器的最上層框架視窗中啟用或停用時，告知控制項。  ATL 實作傳回。|  
|[IOleInPlaceActiveObjectImpl::ResizeBorder](../Topic/IOleInPlaceActiveObjectImpl::ResizeBorder.md)|告知它需要調整其框線的控制項。  ATL 實作會傳回 `S_OK`。|  
|[IOleInPlaceActiveObjectImpl::TranslateAccelerator](../Topic/IOleInPlaceActiveObjectImpl::TranslateAccelerator.md)|處理功能表從容器的快速鍵按鍵訊息。  ATL 實作會傳回 **E\_NOTIMPL**。|  
  
## 備註  
 [IOleInPlaceActiveObject](http://msdn.microsoft.com/library/windows/desktop/ms691299) 介面協助就地控制項與其容器之間的通訊，例如，傳送控制項和容器的作用狀態和通知控制項它需要調整大小。  類別提供 `IOleInPlaceActiveObjectImpl``IOleInPlaceActiveObject` 的預設實作並透過傳送訊息至支援 **IUnknown** 傾印裝置偵錯組建。  
  
 **相關文件** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)， [建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## 繼承階層架構  
 `IOleInPlaceActiveObject`  
  
 `IOleInPlaceActiveObjectImpl`  
  
## 需求  
 **Header:** atlctl.h  
  
## 請參閱  
 [CComControl Class](../../atl/reference/ccomcontrol-class.md)   
 [ActiveX Controls Interfaces](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [Class Overview](../../atl/atl-class-overview.md)