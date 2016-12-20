---
title: "IOleControlImpl Class | Microsoft Docs"
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
  - "IOleControlImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IOleControlImpl class"
ms.assetid: 5a4255ad-ede4-49ca-ba9a-07c2e919fa85
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IOleControlImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會提供 **IOleControl** 介面的預設實作並實作 **IUnknown**。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]執行的應用程式。  
  
## 語法  
  
```  
  
      template< class   
      T  
      >  
class IOleControlImpl  
```  
  
#### 參數  
 `T`  
 您的類別，衍生自 `IOleControlImpl`。  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[IOleControlImpl::FreezeEvents](../Topic/IOleControlImpl::FreezeEvents.md)|指出容器是否忽略或接受來自控制項的事件。|  
|[IOleControlImpl::GetControlInfo](../Topic/IOleControlImpl::GetControlInfo.md)|填入控制項的鍵盤行為的資訊。  ATL 實作會傳回 **E\_NOTIMPL**。|  
|[IOleControlImpl::OnAmbientPropertyChange](../Topic/IOleControlImpl::OnAmbientPropertyChange.md)|告知控制項一或多個容器的環境屬性已變更。  ATL 實作會傳回 `S_OK`。|  
|[IOleControlImpl::OnMnemonic](../Topic/IOleControlImpl::OnMnemonic.md)|通知控制項使用者按下了指定的按鍵。  ATL 實作會傳回 **E\_NOTIMPL**。|  
  
## 備註  
 類別 `IOleControlImpl`[IOleControl](http://msdn.microsoft.com/library/windows/desktop/ms694320) 提供介面的預設實作並透過傳送訊息至實作 **IUnknown** 傾印裝置偵錯組建。  
  
 **相關文件** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)， [建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## 繼承階層架構  
 `IOleControl`  
  
 `IOleControlImpl`  
  
## 需求  
 **Header:** atlctl.h  
  
## 請參閱  
 [IOleObjectImpl Class](../../atl/reference/ioleobjectimpl-class.md)   
 [ActiveX Controls Interfaces](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [Class Overview](../../atl/atl-class-overview.md)