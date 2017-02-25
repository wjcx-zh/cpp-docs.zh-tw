---
title: "IPointerInactiveImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IPointerInactiveImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "inactive objects"
  - "IPointerInactive ATL implementation"
  - "IPointerInactiveImpl class"
ms.assetid: e1fe9ea6-d38a-4527-9112-eb344771e0b7
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# IPointerInactiveImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別的執行 **IUnknown** 和 [IPointerInactive](http://msdn.microsoft.com/library/windows/desktop/ms693712) 介面方法。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]執行的應用程式。  
  
## 語法  
  
```  
  
      template< class   
      T  
      >  
class IPointerInactiveImpl  
```  
  
#### 參數  
 `T`  
 您的類別，衍生自 `IPointerInactiveImpl`。  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[IPointerInactiveImpl::GetActivationPolicy](../Topic/IPointerInactiveImpl::GetActivationPolicy.md)|擷取物件目前的啟動原則。  ATL 實作會傳回 **E\_NOTIMPL**。|  
|[IPointerInactiveImpl::OnInactiveMouseMove](../Topic/IPointerInactiveImpl::OnInactiveMouseMove.md)|告知物件滑鼠指標移動它，表示物件可以引發滑鼠事件。  ATL 實作會傳回 **E\_NOTIMPL**。|  
|[IPointerInactiveImpl::OnInactiveSetCursor](../Topic/IPointerInactiveImpl::OnInactiveSetCursor.md)|設定非作用中物件的滑鼠指標。  ATL 實作會傳回 **E\_NOTIMPL**。|  
  
## 備註  
 非現用物件會載入或執行之一。  不同於現用物件，非作用中物件無法接收視窗滑鼠和鍵盤訊息。  因此，非現用物件使用少數資源並且通常會比較有效率。  
  
 [IPointerInactive](http://msdn.microsoft.com/library/windows/desktop/ms693712) 介面允許物件支援滑鼠互動的最小層級，但仍然非作用中。  這個功能是控制項特別有用。  
  
 將傳回 **E\_NOTIMPL**將 `IPointerInactiveImpl` 實作類別 `IPointerInactive` 方法。  不過，它會將訊息傳送至實作 **IUnknown** 傾印裝置偵錯組建。  
  
 **相關文件** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)， [建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## 繼承階層架構  
 `IPointerInactive`  
  
 `IPointerInactiveImpl`  
  
## 需求  
 **Header:** atlctl.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)