---
title: "IPersistStreamInitImpl Class | Microsoft Docs"
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
  - "ATL::IPersistStreamInitImpl"
  - "ATL::IPersistStreamInitImpl<T>"
  - "ATL.IPersistStreamInitImpl<T>"
  - "IPersistStreamInitImpl"
  - "ATL.IPersistStreamInitImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IPersistStreamInit ATL implementation"
  - "IPersistStreamInitImpl class"
  - "資料流, ATL"
ms.assetid: ef217c3c-020f-4cf8-871e-ef68e57865b8
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IPersistStreamInitImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會實作 **IUnknown** 並提供 [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) 介面的預設實作。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]執行的應用程式。  
  
## 語法  
  
```  
  
      template<  
class T   
>  
class ATL_NO_VTABLE IPersistStreamInitImpl :  
public IPersistStreamInit  
```  
  
#### 參數  
 `T`  
 您的類別，衍生自 `IPersistStreamInitImpl`。  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[IPersistStreamInitImpl::GetClassID](../Topic/IPersistStreamInitImpl::GetClassID.md)|擷取物件的 CLSID。|  
|[IPersistStreamInitImpl::GetSizeMax](../Topic/IPersistStreamInitImpl::GetSizeMax.md)|擷取所需的資料流大小會儲存物件的資料。  ATL 實作會傳回 **E\_NOTIMPL**。|  
|[IPersistStreamInitImpl::InitNew](../Topic/IPersistStreamInitImpl::InitNew.md)|表示初始化新建立的物件。|  
|[IPersistStreamInitImpl::IsDirty](../Topic/IPersistStreamInitImpl::IsDirty.md)|檢查物件的資料是否已變更，自上次儲存。|  
|[IPersistStreamInitImpl::Load](../Topic/IPersistStreamInitImpl::Load.md)|從指定的資料流載入物件的屬性。|  
|[IPersistStreamInitImpl::Save](../Topic/IPersistStreamInitImpl::Save.md)|儲存物件的屬性設定為指定的資料流。|  
  
## 備註  
 [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) 介面允許用戶端要求您的物件載入和儲存其持續性資料至單一資料流。  類別 `IPersistStreamInitImpl` 提供這個介面的預設實作並透過傳送訊息至實作 **IUnknown** 傾印裝置偵錯組建。  
  
 **相關文件** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)， [建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## 繼承階層架構  
 `IPersistStreamInit`  
  
 `IPersistStreamInitImpl`  
  
## 需求  
 **Header:** atlcom.h  
  
## 請參閱  
 [Storages and Streams](http://msdn.microsoft.com/library/windows/desktop/aa380352)   
 [Class Overview](../../atl/atl-class-overview.md)