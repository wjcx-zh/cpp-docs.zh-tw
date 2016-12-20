---
title: "IPropertyPageImpl Class | Microsoft Docs"
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
  - "IPropertyPageImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IPropertyPage ATL implementation"
  - "IPropertyPageImpl class"
  - "屬性頁"
ms.assetid: f9b7c8b1-7a04-4eab-aa63-63efddb740fa
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IPropertyPageImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會實作 **IUnknown** 並提供 [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246) 介面的預設實作。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]執行的應用程式。  
  
## 語法  
  
```  
  
      template< class   
      T  
      >  
class IPropertyPageImpl  
```  
  
#### 參數  
 `T`  
 您的類別，衍生自 `IPropertyPageImpl`。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[IPropertyPageImpl::IPropertyPageImpl](../Topic/IPropertyPageImpl::IPropertyPageImpl.md)|建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[IPropertyPageImpl::Activate](../Topic/IPropertyPageImpl::Activate.md)|建立屬性頁的對話方塊視窗。|  
|[IPropertyPageImpl::Apply](../Topic/IPropertyPageImpl::Apply.md)|將目前的屬性頁值傳遞至 `SetObjects`指定的基礎物件。  ATL 實作會傳回 `S_OK`。|  
|[IPropertyPageImpl::Deactivate](../Topic/IPropertyPageImpl::Deactivate.md)|終結視窗會以 **啟動**。|  
|[IPropertyPageImpl::GetPageInfo](../Topic/IPropertyPageImpl::GetPageInfo.md)|擷取有關屬性頁的詳細資訊。|  
|[IPropertyPageImpl::Help](../Topic/IPropertyPageImpl::Help.md)|叫用屬性頁的 Windows 說明。|  
|[IPropertyPageImpl::IsPageDirty](../Topic/IPropertyPageImpl::IsPageDirty.md)|指示屬性頁是否已變更，自從啟動。|  
|[IPropertyPageImpl::Move](../Topic/IPropertyPageImpl::Move.md)|位置和調整大小屬性頁對話方塊。|  
|[IPropertyPageImpl::SetDirty](../Topic/IPropertyPageImpl::SetDirty.md)|旗標不變更屬性頁的狀態為已變更或。|  
|[IPropertyPageImpl::SetObjects](../Topic/IPropertyPageImpl::SetObjects.md)|提供物件的陣列 **IUnknown** 指標與屬性頁。  這些物件是藉由呼叫接收目前屬性頁值組 **套用**。|  
|[IPropertyPageImpl::SetPageSite](../Topic/IPropertyPageImpl::SetPageSite.md)|提供屬性的網頁。 `IPropertyPageSite` 指標，則屬性頁的屬性架構通訊。|  
|[IPropertyPageImpl::Show](../Topic/IPropertyPageImpl::Show.md)|讓 \[屬性頁\] 對話方塊中可見或不可見的。|  
|[IPropertyPageImpl::TranslateAccelerator](../Topic/IPropertyPageImpl::TranslateAccelerator.md)|處理所指定按鍵。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[IPropertyPageImpl::m\_bDirty](../Topic/IPropertyPageImpl::m_bDirty.md)|指定屬性頁的狀態是否已變更。|  
|[IPropertyPageImpl::m\_dwDocString](../Topic/IPropertyPageImpl::m_dwDocString.md)|儲存資源識別與說明屬性頁的文字字串。|  
|[IPropertyPageImpl::m\_dwHelpContext](../Topic/IPropertyPageImpl::m_dwHelpContext.md)|儲存說明主題的內容識別項與屬性頁。|  
|[IPropertyPageImpl::m\_dwHelpFile](../Topic/IPropertyPageImpl::m_dwHelpFile.md)|儲存資源識別與說明屬性頁的說明檔的名稱。|  
|[IPropertyPageImpl::m\_dwTitle](../Topic/IPropertyPageImpl::m_dwTitle.md)|將資源識別項與出現在 \[屬性\] 頁面的  索引標籤的文字字串。|  
|[IPropertyPageImpl::m\_nObjects](../Topic/IPropertyPageImpl::m_nObjects.md)|儲存的物件數目與屬性頁。|  
|[IPropertyPageImpl::m\_pPageSite](../Topic/IPropertyPageImpl::m_pPageSite.md)|\[屬性頁具有屬性架構通訊的 `IPropertyPageSite` 介面的點。|  
|[IPropertyPageImpl::m\_ppUnk](../Topic/IPropertyPageImpl::m_ppUnk.md)|物件陣列的指向物件的 **IUnknown** 指標與屬性頁。|  
|[IPropertyPageImpl::m\_size](../Topic/IPropertyPageImpl::m_size.md)|以像素為單位\) 儲存屬性頁的  對話方塊的高度和寬度，。|  
  
## 備註  
 [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246) 介面允許物件會在屬性工作表內的特定屬性頁。  類別 `IPropertyPageImpl` 提供這個介面的預設實作並透過傳送訊息至實作 **IUnknown** 傾印裝置偵錯組建。  
  
 **相關文件** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)， [建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## 繼承階層架構  
 `IPropertyPage`  
  
 `IPropertyPageImpl`  
  
## 需求  
 **Header:** atlctl.h  
  
## 請參閱  
 [IPropertyPage2Impl Class](../../atl/reference/ipropertypage2impl-class.md)   
 [IPerPropertyBrowsingImpl Class](../../atl/reference/iperpropertybrowsingimpl-class.md)   
 [ISpecifyPropertyPagesImpl Class](../../atl/reference/ispecifypropertypagesimpl-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)