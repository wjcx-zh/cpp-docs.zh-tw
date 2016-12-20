---
title: "IOleInPlaceObjectWindowlessImpl Class | Microsoft Docs"
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
  - "IOleInPlaceObjectWindowlessImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "activation [C++], ATL"
  - "ActiveX 控制項 [C++], communication between container and control"
  - "控制項 [ATL], windowless"
  - "deactivating ATL"
  - "IOleInPlaceObjectWindowless, ATL 實作"
  - "IOleInPlaceObjectWindowlessImpl class"
ms.assetid: a2e0feb4-bc59-4adf-aab2-105457bbdbb4
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IOleInPlaceObjectWindowlessImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會實作 **IUnknown** 並提供讓無視窗 \(Windowless\) 控制項接收 Windows 訊息和參與拖放作業的方法。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]執行的應用程式。  
  
## 語法  
  
```  
  
      template< class   
      T  
      >  
class IOleInPlaceObjectWindowlessImpl  
```  
  
#### 參數  
 `T`  
 您的類別，衍生自 `IOleInPlaceObjectWindowlessImpl`。  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp](../Topic/IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp.md)|啟用即時線上說明。  ATL 實作會傳回 **E\_NOTIMPL**。|  
|[IOleInPlaceObjectWindowlessImpl::GetDropTarget](../Topic/IOleInPlaceObjectWindowlessImpl::GetDropTarget.md)|提供示範就地啟動，無視窗物件的 `IDropTarget` 介面支援拖放。  ATL 實作會傳回 **E\_NOTIMPL**。|  
|[IOleInPlaceObjectWindowlessImpl::GetWindow](../Topic/IOleInPlaceObjectWindowlessImpl::GetWindow.md)|取得視窗控制代碼。|  
|[IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate](../Topic/IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate.md)|停用就地現用控制項。|  
|[IOleInPlaceObjectWindowlessImpl::OnWindowMessage](../Topic/IOleInPlaceObjectWindowlessImpl::OnWindowMessage.md)|分派容器的訊息至是就地啟動的無視窗 \(Windowless\) 控制項。|  
|[IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo](../Topic/IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo.md)|重新啟動之前已停用的控制項。  ATL 實作會傳回 **E\_NOTIMPL**。|  
|[IOleInPlaceObjectWindowlessImpl::SetObjectRects](../Topic/IOleInPlaceObjectWindowlessImpl::SetObjectRects.md)|表示矩形控制項的哪些部分是可見的。|  
|[IOleInPlaceObjectWindowlessImpl::UIDeactivate](../Topic/IOleInPlaceObjectWindowlessImpl::UIDeactivate.md)|停用和移除支援就地啟動的使用者介面。|  
  
## 備註  
 [IOleInPlaceObject](http://msdn.microsoft.com/library/windows/desktop/ms692646) 介面處理控制項的就地重新啟動和停用並決定控制項應該是可見的。  介面可讓 [IOleInPlaceObjectWindowless](http://msdn.microsoft.com/library/windows/desktop/ms687304) 無視窗 \(Windowless\) 控制項接收 Windows 訊息和參與拖放作業。  類別提供 `IOleInPlaceObjectWindowlessImpl``IOleInPlaceObject` 和 `IOleInPlaceObjectWindowless` 的預設實作並透過傳送訊息至實作 **IUnknown** 傾印裝置偵錯組建。  
  
 **相關文件** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)， [建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## 繼承階層架構  
 `IOleInPlaceObjectWindowless`  
  
 `IOleInPlaceObjectWindowlessImpl`  
  
## 需求  
 **Header:** atlctl.h  
  
## 請參閱  
 [CComControl Class](../../atl/reference/ccomcontrol-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)