---
title: "IPersistStorageImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::IPersistStorageImpl"
  - "ATL::IPersistStorageImpl<T>"
  - "ATL.IPersistStorageImpl<T>"
  - "IPersistStorageImpl"
  - "ATL.IPersistStorageImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IPersistStorageImpl class"
  - "儲存體, ATL"
ms.assetid: d652f02c-239c-47c7-9a50-3e9fc3014fff
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# IPersistStorageImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會實作介面 [IPersistStorage](http://msdn.microsoft.com/library/windows/desktop/ms679731) 。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]執行的應用程式。  
  
## 語法  
  
```  
  
      template <  
class T  
>  
class ATL_NO_VTABLE IPersistStorageImpl :  
public IPersistStorage  
```  
  
#### 參數  
 `T`  
 您的類別，衍生自 `IPersistStorageImpl`。  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[IPersistStorageImpl::GetClassID](../Topic/IPersistStorageImpl::GetClassID.md)|擷取物件的 CLSID。|  
|[IPersistStorageImpl::HandsOffStorage](../Topic/IPersistStorageImpl::HandsOffStorage.md)|指示物件釋放所有儲存物件和輸入 HandsOff 模式。  ATL 實作會傳回 `S_OK`。|  
|[IPersistStorageImpl::InitNew](../Topic/IPersistStorageImpl::InitNew.md)|初始化新的儲存區。|  
|[IPersistStorageImpl::IsDirty](../Topic/IPersistStorageImpl::IsDirty.md)|檢查物件的資料是否已變更，自上次儲存。|  
|[IPersistStorageImpl::Load](../Topic/IPersistStorageImpl::Load.md)|從指定的儲存體載入物件的屬性。|  
|[IPersistStorageImpl::Save](../Topic/IPersistStorageImpl::Save.md)|儲存物件的屬性設定為指定的儲存區。|  
|[IPersistStorageImpl::SaveCompleted](../Topic/IPersistStorageImpl::SaveCompleted.md)|告知物件就可以回到一般模式\)、將它儲存物件。  ATL 實作會傳回 `S_OK`。|  
  
## 備註  
 `IPersistStorageImpl` [IPersistStorage](http://msdn.microsoft.com/library/windows/desktop/ms679731) 實作介面，則會使用儲存區，可讓用戶端要求您的物件載入和儲存其持續性資料。  
  
 這個類別的實作需要類別 `T` 進行實作 `IPersistStreamInit` 介面可透過 `QueryInterface`。  這通常表示類別 `T` 應該從 [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)衍生自類別，在 [COM 對應](../Topic/BEGIN_COM_MAP.md)的 `IPersistStreamInit` 提供輸入和使用 [屬性對應](../Topic/BEGIN_PROP_MAP.md) 描述類別的持續性資料。  
  
 **相關文件** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)， [建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## 繼承階層架構  
 `IPersistStorage`  
  
 `IPersistStorageImpl`  
  
## 需求  
 **Header:** atlcom.h  
  
## 請參閱  
 [Storages and Streams](http://msdn.microsoft.com/library/windows/desktop/aa380352)   
 [IPersistStreamInitImpl Class](../../atl/reference/ipersiststreaminitimpl-class.md)   
 [IPersistPropertyBagImpl Class](../../atl/reference/ipersistpropertybagimpl-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)