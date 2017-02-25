---
title: "IPersistPropertyBagImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IPersistPropertyBagImpl"
  - "ATL.IPersistPropertyBagImpl<T>"
  - "ATL::IPersistPropertyBagImpl"
  - "ATL::IPersistPropertyBagImpl<T>"
  - "ATL.IPersistPropertyBagImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IPersistPropertyBagImpl class"
ms.assetid: 712af24d-99f8-40f2-9811-53b3ff6e5b19
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# IPersistPropertyBagImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會實作 **IUnknown** 並且讓物件將其屬性設定為其中一個用戶端所提供的屬性包。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]執行的應用程式。  
  
## 語法  
  
```  
  
      template <   
class T   
>  
class ATL_NO_VTABLE IPersistPropertyBagImpl :  
public IPersistPropertyBag  
```  
  
#### 參數  
 `T`  
 您的類別，衍生自 `IPersistPropertyBagImpl`。  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[IPersistPropertyBagImpl::GetClassID](../Topic/IPersistPropertyBagImpl::GetClassID.md)|擷取物件的 CLSID。|  
|[IPersistPropertyBagImpl::InitNew](../Topic/IPersistPropertyBagImpl::InitNew.md)|表示初始化新建立的物件。  ATL 實作會傳回 `S_OK`。|  
|[IPersistPropertyBagImpl::Load](../Topic/IPersistPropertyBagImpl::Load.md)|從一個用戶端所提供的屬性包載入物件的屬性。|  
|[IPersistPropertyBagImpl::Save](../Topic/IPersistPropertyBagImpl::Save.md)|儲存物件的所有屬性集合於一個用戶端所提供的屬性包。|  
  
## 備註  
 [IPersistPropertyBag](https://msdn.microsoft.com/en-us/library/aa768205.aspx) 介面可以讓物件儲存的屬性加入至用戶端所提供的屬性包。  類別 `IPersistPropertyBagImpl` 提供這個介面的預設實作並透過傳送訊息至實作 **IUnknown** 傾印裝置偵錯組建。  
  
 **IPersistPropertyBag** 與 [IPropertyBag](https://msdn.microsoft.com/en-us/library/aa768196.aspx) 和 [IErrorLog](https://msdn.microsoft.com/en-us/library/aa768231.aspx)一起運作。  介面必須由用戶端實作後者這兩個介面。  藉由 `IPropertyBag`，用戶端會儲存及載入物件的個別屬性。  藉由 **IErrorLog**物件，而用戶端可以報告時所遇到的任何錯誤。  
  
 **相關文件** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)， [建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## 繼承階層架構  
 `IPersistPropertyBag`  
  
 `IPersistPropertyBagImpl`  
  
## 需求  
 **Header:** atlcom.h  
  
## 請參閱  
 [BEGIN\_PROP\_MAP](../Topic/BEGIN_PROP_MAP.md)   
 [Class Overview](../../atl/atl-class-overview.md)