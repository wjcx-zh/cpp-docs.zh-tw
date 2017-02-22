---
title: "IRunnableObjectImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IRunnableObjectImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "容器, running controls"
  - "控制項 [ATL], 執行"
  - "控制項 [C++], container running in ATL"
  - "IRunnableObject, ATL 實作"
  - "IRunnableObjectImpl class"
ms.assetid: 305c7c3b-889e-49dd-aca1-34379c1b9931
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# IRunnableObjectImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會實作 **IUnknown** 並提供 [IRunnableObject](http://msdn.microsoft.com/library/windows/desktop/ms692783) 介面的預設實作。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]執行的應用程式。  
  
## 語法  
  
```  
  
      template< class   
      T  
      >  
class IRunnableObjectImpl  
```  
  
#### 參數  
 `T`  
 您的類別，衍生自 `IRunnableObjectImpl`。  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[IRunnableObjectImpl::GetRunningClass](../Topic/IRunnableObjectImpl::GetRunningClass.md)|傳回執行控制項的 CLSID。  ATL 實作設定 CLSID。 `GUID_NULL` 並傳回 **E\_UNEXPECTED**。|  
|[IRunnableObjectImpl::IsRunning](../Topic/IRunnableObjectImpl::IsRunning.md)|判斷控制項是否正在執行。  ATL 實作會傳回 **是**。|  
|[IRunnableObjectImpl::LockRunning](../Topic/IRunnableObjectImpl::LockRunning.md)|鎖定控制項放入行動狀態。  ATL 實作會傳回 `S_OK`。|  
|[IRunnableObjectImpl::Run](../Topic/IRunnableObjectImpl::Run.md)|強制控制項執行。  ATL 實作會傳回 `S_OK`。|  
|[IRunnableObjectImpl::SetContainedObject](../Topic/IRunnableObjectImpl::SetContainedObject.md)|表示嵌入該控制項。  ATL 實作會傳回 `S_OK`。|  
  
## 備註  
 [IRunnableObject](http://msdn.microsoft.com/library/windows/desktop/ms692783) 介面可讓容器判斷控制項是否正在執行，會強制其執行或鎖定它的目前的狀態。  類別 `IRunnableObjectImpl` 提供這個介面的預設實作並透過傳送訊息至實作 **IUnknown** 傾印裝置偵錯組建。  
  
 **相關文件** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)， [建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## 繼承階層架構  
 `IRunnableObject`  
  
 `IRunnableObjectImpl`  
  
## 需求  
 **Header:** atlctl.h  
  
## 請參閱  
 [CComControl Class](../../atl/reference/ccomcontrol-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)