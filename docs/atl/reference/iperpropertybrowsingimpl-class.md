---
title: "IPerPropertyBrowsingImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.IPerPropertyBrowsingImpl"
  - "IPerPropertyBrowsing"
  - "ATL::IPerPropertyBrowsingImpl"
  - "ATL::IPerPropertyBrowsingImpl<T>"
  - "IPerPropertyBrowsingImpl"
  - "ATL.IPerPropertyBrowsingImpl<T>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IPerPropertyBrowsing, ATL 實作"
  - "IPerPropertyBrowsingImpl class"
  - "屬性頁, accessing information"
ms.assetid: 0b1a9be3-d242-4767-be69-663a21e4b728
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# IPerPropertyBrowsingImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會實作 **IUnknown** 並允許用戶端存取物件之屬性頁的詳細資訊。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]執行的應用程式。  
  
## 語法  
  
```  
  
      template<  
class T   
>  
class ATL_NO_VTABLE IPerPropertyBrowsingImpl :  
public IPerPropertyBrowsing  
```  
  
#### 參數  
 `T`  
 您的類別，衍生自 `IPerPropertyBrowsingImpl`。  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[IPerPropertyBrowsingImpl::GetDisplayString](../Topic/IPerPropertyBrowsingImpl::GetDisplayString.md)|擷取描述指定之屬性的字串。|  
|[IPerPropertyBrowsingImpl::GetPredefinedStrings](../Topic/IPerPropertyBrowsingImpl::GetPredefinedStrings.md)|擷取字串陣列具有特定屬性可以接受的值對應。|  
|[IPerPropertyBrowsingImpl::GetPredefinedValue](../Topic/IPerPropertyBrowsingImpl::GetPredefinedValue.md)|擷取包含屬性的值 **VARIANT** 由指定的 DISPID。  物件與 `GetPredefinedStrings`擷取的字串名稱。  ATL 實作會傳回 **E\_NOTIMPL**。|  
|[IPerPropertyBrowsingImpl::MapPropertyToPage](../Topic/IPerPropertyBrowsingImpl::MapPropertyToPage.md)|擷取屬性頁的 CLSID 與特定屬性。|  
  
## 備註  
 [IPerPropertyBrowsing](http://msdn.microsoft.com/library/windows/desktop/ms678432) 介面允許用戶端存取物件之屬性頁的詳細資訊。  類別 `IPerPropertyBrowsingImpl` 提供這個介面的預設實作並透過傳送訊息至實作 **IUnknown** 傾印裝置偵錯組建。  
  
> [!NOTE]
>  如果您使用的是 Microsoft Access 當做容器應用程式，您必須從 `IPerPropertyBrowsingImpl`衍生您的類別。  否則，存取不會載入您的控制項。  
  
 **相關文件** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)， [建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## 繼承階層架構  
 `IPerPropertyBrowsing`  
  
 `IPerPropertyBrowsingImpl`  
  
## 需求  
 **Header:** atlctl.h  
  
## 請參閱  
 [IPropertyPageImpl Class](../../atl/reference/ipropertypageimpl-class.md)   
 [ISpecifyPropertyPagesImpl Class](../../atl/reference/ispecifypropertypagesimpl-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)