---
title: "CComClassFactory Class | Microsoft Docs"
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
  - "ATL.CComClassFactory"
  - "CComClassFactory"
  - "ATL::CComClassFactory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComClassFactory class"
ms.assetid: e56dacf7-d5c4-4c42-aef4-a86d91981a1b
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComClassFactory Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會實作介面 [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) 。  
  
## 語法  
  
```  
  
   class CComClassFactory : public IClassFactory,   
public CComObjectRootEx< CComGlobalsThreadModel >  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComClassFactory::CreateInstance](../Topic/CComClassFactory::CreateInstance.md)|建立指定的 CLSID 的物件。|  
|[CComClassFactory::LockServer](../Topic/CComClassFactory::LockServer.md)|鎖定在記憶體的 Class Factory。|  
  
## 備註  
 `CComClassFactory` 實作 [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) 介面，包含建立的特定 CLSID 物件的方法，以及鎖定在記憶體的 Class Factory 可以快速建立新的物件。  必須為您在系統登錄中，而對的每個類別實作**IClassFactory** 已指派 CLSID。  
  
 ATL 物件以下列方式通常是安全的 Class Factory。 [CComCoClass](../../atl/reference/ccomcoclass-class.md)。  這個類別包含巨集 [DECLARE\_CLASSFACTORY](../Topic/DECLARE_CLASSFACTORY.md)，宣告 `CComClassFactory` 做為預設的 Class Factory。  若要覆寫這項預設，請指定 `DECLARE_CLASSFACTORY`*XXX* 巨集是在您的類別定義。  例如， [DECLARE\_CLASSFACTORY\_EX](../Topic/DECLARE_CLASSFACTORY_EX.md) 巨集為 Class Factory 會使用指定的類別:  
  
 [!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/CPP/ccomclassfactory-class_1.h)]  
  
 上述類別定義指定 **CMyClassFactory** 就會做為物件的預設 Class Factory。  **CMyClassFactory** 必須從 `CComClassFactory` 衍生並覆寫 `CreateInstance`。  
  
 ATL 提供宣告 Class Factory 的其他三個巨集:  
  
-   [DECLARE\_ CLASSFACTORY2](../Topic/DECLARE_CLASSFACTORY2.md) 使用 [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)，透過授權控制項建立。  
  
-   [DECLARE\_CLASSFACTORY\_AUTO\_THREAD](../Topic/DECLARE_CLASSFACTORY_AUTO_THREAD.md) 使用 [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)，建立多個 Apartment 內的物件。  
  
-   [DECLARE\_CLASSFACTORY\_SINGLETON](../Topic/DECLARE_CLASSFACTORY_SINGLETON.md) 使用 [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)，建構 [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) 單一物件。  
  
## 需求  
 **Header:** atlcom.h  
  
## 請參閱  
 [CComObjectRootEx Class](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](../Topic/CComGlobalsThreadModel.md)   
 [Class Overview](../../atl/atl-class-overview.md)