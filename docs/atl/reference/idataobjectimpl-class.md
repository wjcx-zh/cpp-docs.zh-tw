---
title: "IDataObjectImpl Class | Microsoft Docs"
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
  - "IDataObjectImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "data transfer [C++]"
  - "data transfer [C++], Uniform Data Transfer"
  - "IDataObject, ATL 實作"
  - "IDataObjectImpl class"
ms.assetid: b680f0f7-7795-40a1-a0f6-f48768201c89
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IDataObjectImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會提供對支援制式資料傳輸和管理連接的方法。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]執行的應用程式。  
  
## 語法  
  
```  
  
      template< class   
      T  
      >  
class IDataObjectImpl  
```  
  
#### 參數  
 `T`  
 您的類別，衍生自 `IDataObjectImpl`。  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[IDataObjectImpl::DAdvise](../Topic/IDataObjectImpl::DAdvise.md)|建立資料物件和通知接收之間的連接。  這可讓通知接收的接收變更告知在物件上的。|  
|[IDataObjectImpl::DUnadvise](../Topic/IDataObjectImpl::DUnadvise.md)|結束藉由 `DAdvise`先前建立的連接。|  
|[IDataObjectImpl::EnumDAdvise](../Topic/IDataObjectImpl::EnumDAdvise.md)|建立列舉程式以逐一查看目前的諮詢連接。|  
|[IDataObjectImpl::EnumFormatEtc](../Topic/IDataObjectImpl::EnumFormatEtc.md)|建立列舉值傳遞資料物件所支援的 **FORMATETC** 結構逐一查看。  ATL 實作會傳回 **E\_NOTIMPL**。|  
|[IDataObjectImpl::FireDataChange](../Topic/IDataObjectImpl::FireDataChange.md)|將變更告知給每一位通知接收。|  
|[IDataObjectImpl::GetCanonicalFormatEtc](../Topic/IDataObjectImpl::GetCanonicalFormatEtc.md)|擷取一個邏輯上相等的 **FORMATETC** 結構至更複雜的一個。  ATL 實作會傳回 **E\_NOTIMPL**。|  
|[IDataObjectImpl::GetData](../Topic/IDataObjectImpl::GetData.md)|將資料從資料物件傳送至用戶端。  在資料 **FORMATETC** 結構描述和傳遞 **STGMEDIUM** 結構傳輸。|  
|[IDataObjectImpl::GetDataHere](../Topic/IDataObjectImpl::GetDataHere.md)|`GetData`類似，不同之處在於，用戶端必須配置 **STGMEDIUM** 結構。  ATL 實作會傳回 **E\_NOTIMPL**。|  
|[IDataObjectImpl::QueryGetData](../Topic/IDataObjectImpl::QueryGetData.md)|判斷資料物件是否支援傳輸資料的特定 **FORMATETC** 結構。  ATL 實作會傳回 **E\_NOTIMPL**。|  
|[IDataObjectImpl::SetData](../Topic/IDataObjectImpl::SetData.md)|將資料從用戶端傳送至資料物件。  ATL 實作會傳回 **E\_NOTIMPL**。|  
  
## 備註  
 [IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421) 介面提供方法來支援制式資料傳輸。  `IDataObject` 使用標準格式結構 [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) 和 [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) 擷取和儲存資料。  
  
 `IDataObject` 也會嘗試連接通知接收處理資料變更告知。  為了讓用戶端可以接收資料從資料物件變更告知，用戶端必須實作呼叫通知接收的物件的 [IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513) 介面。  當用戶端呼叫 **IDataObject::DAdvise**時，連接就會建立資料物件和通知接收之間。  
  
 類別提供 `IDataObjectImpl``IDataObject` 的預設實作並透過傳送訊息至實作 **IUnknown** 傾印裝置偵錯組建。  
  
 **相關文件** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)， [建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## 繼承階層架構  
 `IDataObject`  
  
 `IDataObjectImpl`  
  
## 需求  
 **Header:** atlctl.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)