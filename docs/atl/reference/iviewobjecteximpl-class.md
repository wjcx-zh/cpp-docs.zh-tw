---
title: "IViewObjectExImpl Class | Microsoft Docs"
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
  - "ATL::IViewObjectExImpl<T>"
  - "ATL.IViewObjectExImpl"
  - "ATL::IViewObjectExImpl"
  - "ATL.IViewObjectExImpl<T>"
  - "IViewObjectExImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控制項 [C++], 繪製"
  - "advise sinks"
  - "IViewObjectEx ATL implementation"
  - "IViewObjectExImpl class"
ms.assetid: ad6de760-1ee5-4883-b033-ae57beffc369
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IViewObjectExImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會實作 **IUnknown** 並提供 [IViewObject](http://msdn.microsoft.com/library/windows/desktop/ms680763)、 [IViewObject2](http://msdn.microsoft.com/library/windows/desktop/ms691318)和 [IViewObjectEx](http://msdn.microsoft.com/library/windows/desktop/ms682375) 介面的預設實作。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]執行的應用程式。  
  
## 語法  
  
```  
  
      template<  
class T   
>  
class ATL_NO_VTABLE IViewObjectExImpl :  
public IViewObjectEx  
```  
  
#### 參數  
 `T`  
 您的類別，衍生自 `IViewObjectExImpl`。  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[IViewObjectExImpl::Draw](../Topic/IViewObjectExImpl::Draw.md)|繪製控制項的表示在裝置內容中。|  
|[IViewObjectExImpl::Freeze](../Topic/IViewObjectExImpl::Freeze.md)|凍結控制項繪製表示，所以不會變更之前 `Unfreeze`。  ATL 實作會傳回 **E\_NOTIMPL**。|  
|[IViewObjectExImpl::GetAdvise](../Topic/IViewObjectExImpl::GetAdvise.md)|如果有的話，擷取控制項的現有諮詢接收連接。|  
|[IViewObjectExImpl::GetColorSet](../Topic/IViewObjectExImpl::GetColorSet.md)|傳回控制項所使用的邏輯調色盤用於繪製。  ATL 實作會傳回 **E\_NOTIMPL**。|  
|[IViewObjectExImpl::GetExtent](../Topic/IViewObjectExImpl::GetExtent.md)|從控制項類別資料成員 [CComControlBase::m\_sizeExtent](../Topic/CComControlBase::m_sizeExtent.md)擷取在 HIMETRIC 單位 \(每個單位為 0.01 公釐顯示控制項的大小\)。|  
|[IViewObjectExImpl::GetNaturalExtent](../Topic/IViewObjectExImpl::GetNaturalExtent.md)|指定要使用的物件提供從容器的縮放，提示使用者進行調整。|  
|[IViewObjectExImpl::GetRect](../Topic/IViewObjectExImpl::GetRect.md)|傳回描述一個要求的繪製方面的矩形。  ATL 實作會傳回 **E\_NOTIMPL**。|  
|[IViewObjectExImpl::GetViewStatus](../Topic/IViewObjectExImpl::GetViewStatus.md)|如需物件的不透明的傳回資訊，以及繪圖方面支援。|  
|[IViewObjectExImpl::QueryHitPoint](../Topic/IViewObjectExImpl::QueryHitPoint.md)|檢查指定的點是否包含在指定的矩形並傳回在 `pHitResult`的 [HITRESULT](http://msdn.microsoft.com/library/windows/desktop/ms682187) 值。|  
|[IViewObjectExImpl::QueryHitRect](../Topic/IViewObjectExImpl::QueryHitRect.md)|檢查控制項的顯示矩形是否重疊位於指定位置的矩形的任何位置並傳回在 `pHitResult`的 **HITRESULT** 值。|  
|[IViewObjectExImpl::SetAdvise](../Topic/IViewObjectExImpl::SetAdvise.md)|將控制項和通知接收之間的連接，因此可以接收會收到有關在控制項檢視中的變更。|  
|[IViewObjectExImpl::Unfreeze](../Topic/IViewObjectExImpl::Unfreeze.md)|解除凍結控制項繪製的表示。  ATL 實作會傳回 **E\_NOTIMPL**。|  
  
## 備註  
 [IViewObject](http://msdn.microsoft.com/library/windows/desktop/ms680763)、 [IViewObject2](http://msdn.microsoft.com/library/windows/desktop/ms691318)和 [IViewObjectEx](http://msdn.microsoft.com/library/windows/desktop/ms682375) 介面可讓控制項直接顯示和建立並嘗試通知接收告知容器控制項中顯示的變更。  **IViewObjectEx** 介面為擴充的控制項功能的支援 \(例如重繪閃動可用的繪圖、非矩形和透明控制項和點擊測試 \(例如，關閉滑鼠點選方式在控制項中必須要考慮\)。  類別 `IViewObjectExImpl` 提供這些介面的預設實作並透過傳送訊息至實作 **IUnknown** 傾印裝置偵錯組建。  
  
## 繼承階層架構  
 `IViewObjectEx`  
  
 `IViewObjectExImpl`  
  
## 需求  
 **Header:** atlctl.h  
  
## 請參閱  
 [CComControl Class](../../atl/reference/ccomcontrol-class.md)   
 [ActiveX Controls Interfaces](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [教學課程](../../atl/active-template-library-atl-tutorial.md)   
 [建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)   
 [Class Overview](../../atl/atl-class-overview.md)