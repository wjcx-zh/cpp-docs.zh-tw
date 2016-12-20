---
title: "CBindStatusCallback Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CBindStatusCallback"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "asynchronous data transfer [C++]"
  - "CBindStatusCallback class"
  - "data transfer [C++]"
  - "data transfer [C++], 非同步"
ms.assetid: 0f5da276-6031-4418-b2a9-a4750ef29e77
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CBindStatusCallback Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會實作 `IBindStatusCallback` 介面。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
      template <class   
      T  
      , int   
      nBindFlags  
      = BINDF_ASYNCHRONOUS |   
BINDF_ASYNCSTORAGE | BINDF_GETNEWESTVERSION | BINDF_NOWRITECACHE>  
class ATL_NO_VTABLE CBindStatusCallback : public CComObjectRootEx  
<T::_ThreadModel::ThreadModelNoCS>, public IBindStatusCallbackImpl<T>   
```  
  
#### 參數  
 `T`  
 您的包含呼叫做為資料的函式類別接收。  
  
 *nBindFlags*  
 指定由 [GetBindInfo](../Topic/CBindStatusCallback::GetBindInfo.md)傳回的繫結旗標。  預設實作會將繫結是非同步的，擷取資料或物件的新版本並不在磁碟快取存放所擷取的資料。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CBindStatusCallback::CBindStatusCallback](../Topic/CBindStatusCallback::CBindStatusCallback.md)|建構函式。|  
|[CBindStatusCallback::~CBindStatusCallback](../Topic/CBindStatusCallback::~CBindStatusCallback.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CBindStatusCallback::Download](../Topic/CBindStatusCallback::Download.md)|啟動下載流程 `CBindStatusCallback` ，建立物件，並呼叫 `StartAsyncDownload`的靜態方法。|  
|[CBindStatusCallback::GetBindInfo](../Topic/CBindStatusCallback::GetBindInfo.md)|呼叫非同步的 Moniker 所需將建立的繫結型別的資訊。|  
|[CBindStatusCallback::GetPriority](../Topic/CBindStatusCallback::GetPriority.md)|呼叫非同步取得 Moniker 繫結作業的優先權。  ATL 實作會傳回 `E_NOTIMPL`。|  
|[CBindStatusCallback::OnDataAvailable](../Topic/CBindStatusCallback::OnDataAvailable.md)|呼叫將資料提供給您的應用程式，它會變成可用狀態。  讀取資料，然後呼叫函式以使用資料。|  
|[CBindStatusCallback::OnLowResource](../Topic/CBindStatusCallback::OnLowResource.md)|呼叫時，資源不足。  ATL 實作會傳回 `S_OK`。|  
|[CBindStatusCallback::OnObjectAvailable](../Topic/CBindStatusCallback::OnObjectAvailable.md)|呼叫非同步的 Moniker 傳遞物件介面指標到您的應用程式。  ATL 實作會傳回 `S_OK`。|  
|[CBindStatusCallback::OnProgress](../Topic/CBindStatusCallback::OnProgress.md)|呼叫以指示資料下載流程的進度。  ATL 實作會傳回 `S_OK`。|  
|[CBindStatusCallback::OnStartBinding](../Topic/CBindStatusCallback::OnStartBinding.md)|呼叫，在繫結時啟動。|  
|[CBindStatusCallback::OnStopBinding](../Topic/CBindStatusCallback::OnStopBinding.md)|呼叫時，非同步傳送資料已停止。|  
|[CBindStatusCallback::StartAsyncDownload](../Topic/CBindStatusCallback::StartAsyncDownload.md)|使用中可用的位元組，並讀取位元組為零，會從 URL 中建立推入型資料流物件，並呼叫 `OnDataAvailable` ，在資料可供讀取時。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CBindStatusCallback::m\_dwAvailableToRead](../Topic/CBindStatusCallback::m_dwAvailableToRead.md)|可供讀取的位元組數目。|  
|[CBindStatusCallback::m\_dwTotalRead](../Topic/CBindStatusCallback::m_dwTotalRead.md)|讀取的位元組總數。|  
|[CBindStatusCallback::m\_pFunc](../Topic/CBindStatusCallback::m_pFunc.md)|由所呼叫之函式的指標，當資料可供使用。|  
|[CBindStatusCallback::m\_pT](../Topic/CBindStatusCallback::m_pT.md)|物件的指標要求非同步傳送資料的。|  
|[CBindStatusCallback::m\_spBindCtx](../Topic/CBindStatusCallback::m_spBindCtx.md)|為 [IBindCtx](http://msdn.microsoft.com/library/windows/desktop/ms693755) 介面的指標目前繫結作業的。|  
|[CBindStatusCallback::m\_spBinding](../Topic/CBindStatusCallback::m_spBinding.md)|為 `IBinding` 介面的指標目前繫結作業的。|  
|[CBindStatusCallback::m\_spMoniker](../Topic/CBindStatusCallback::m_spMoniker.md)|為 [IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705) 介面指標的 URL 來使用。|  
|[CBindStatusCallback::m\_spStream](../Topic/CBindStatusCallback::m_spStream.md)|為 [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) 介面的指標傳送資料的。|  
  
## 備註  
 `CBindStatusCallback` 類別會實作 `IBindStatusCallback` 介面。  必須由應用程式實作`IBindStatusCallback` ，因此可能會從將資料非同步地傳送的告知。  系統提供的非同步 Moniker 使用 `IBindStatusCallback` 方法與您的物件傳送和收到非同步傳送資料的資訊。  
  
 通常， `CBindStatusCallback` 物件與特定的繫結作業。  例如，在 [ASYNC](../../top/visual-cpp-samples.md) 範例，因此，當您設定 URL 屬性，則會在呼叫上 `CBindStatusCallback` 物件 `Download`:  
  
 [!code-cpp[NVC_ATL_Windowing#86](../../atl/codesnippet/CPP/cbindstatuscallback-class_1.h)]  
  
 會有資料時，非同步 Moniker 使用回呼函式 `OnData` 呼叫您的應用程式。  系統會提供非同步的 Moniker。  
  
## 繼承階層架構  
 `CComObjectRootBase`  
  
 `IBindStatusCallback`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `CBindStatusCallback`  
  
## 需求  
 **Header:** atlctl.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)