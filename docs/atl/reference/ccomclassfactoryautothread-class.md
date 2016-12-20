---
title: "CComClassFactoryAutoThread Class | Microsoft Docs"
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
  - "ATL::CComClassFactoryAutoThread"
  - "ATL.CComClassFactoryAutoThread"
  - "CComClassFactoryAutoThread"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComClassFactoryAutoThread class"
ms.assetid: 22008042-533f-4dd9-bf7e-191ee571f9a1
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComClassFactoryAutoThread Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別是在多個 Apartment [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) 實作介面，並允許建立物件。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
      class CComClassFactoryAutoThread : public IClassFactory,   
public CComObjectRootEx< CComGlobalsThreadModel >  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComClassFactoryAutoThread::CreateInstance](../Topic/CComClassFactoryAutoThread::CreateInstance.md)|建立指定的 CLSID 的物件。|  
|[CComClassFactoryAutoThread::LockServer](../Topic/CComClassFactoryAutoThread::LockServer.md)|鎖定在記憶體的 Class Factory。|  
  
## 備註  
 `CComClassFactoryAutoThread` 類似， [CComClassFactory](../../atl/reference/ccomclassfactory-class.md)，但允許物件建立多個 Apartment。  若要使用這項支援，從 [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)衍生您的 EXE 模組。  
  
 ATL 物件以下列方式通常是安全的 Class Factory。 [CComCoClass](../../atl/reference/ccomcoclass-class.md)。  這個類別包含巨集 [DECLARE\_CLASSFACTORY](../Topic/DECLARE_CLASSFACTORY.md)，宣告 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) 做為預設的 Class Factory。  若要使用 `CComClassFactoryAutoThread`，請指定 [DECLARE\_CLASSFACTORY\_AUTO\_THREAD](../Topic/DECLARE_CLASSFACTORY_AUTO_THREAD.md) 巨集在物件的類別定義。  例如：  
  
 [!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/CPP/ccomclassfactoryautothread-class_1.h)]  
  
## 繼承階層架構  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IClassFactory`  
  
 `CComClassFactoryAutoThread`  
  
## 需求  
 **Header:** atlcom.h  
  
## 請參閱  
 [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)   
 [CComClassFactory2 Class](../../atl/reference/ccomclassfactory2-class.md)   
 [CComClassFactorySingleton Class](../../atl/reference/ccomclassfactorysingleton-class.md)   
 [CComObjectRootEx Class](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](../Topic/CComGlobalsThreadModel.md)   
 [Class Overview](../../atl/atl-class-overview.md)