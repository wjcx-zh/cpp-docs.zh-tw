---
title: "CComClassFactorySingleton Class | Microsoft Docs"
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
  - "ATL.CComClassFactorySingleton"
  - "ATL.CComClassFactorySingleton<T>"
  - "ATL::CComClassFactorySingleton"
  - "ATL::CComClassFactorySingleton<T>"
  - "CComClassFactorySingleton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComClassFactorySingleton class"
ms.assetid: debb983c-382b-487b-8d42-7ea26dc158b8
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComClassFactorySingleton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會從 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) 衍生並使用 [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) 建構單一物件。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
      template<  
class T  
>  
class CComClassFactorySingleton :  
public CComClassFactory  
```  
  
#### 參數  
 `T`  
 您的類別。  
  
 `CComClassFactorySingleton` [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) 從衍生並使用 [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) 建構單一物件。  為 `CreateInstance` 每次呼叫方法都將查詢介面指標的這個物件。  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComClassFactorySingleton::CreateInstance](../Topic/CComClassFactorySingleton::CreateInstance.md)|查詢介面指標的 `m_spObj` 。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CComClassFactorySingleton::m\_spObj](../Topic/CComClassFactorySingleton::m_spObj.md)|`CComClassFactorySingleton` [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) 建構的物件。|  
  
## 備註  
 ATL 物件以下列方式通常是安全的 Class Factory。 [CComCoClass](../../atl/reference/ccomcoclass-class.md)。  這個類別包含巨集 [DECLARE\_CLASSFACTORY](../Topic/DECLARE_CLASSFACTORY.md)，宣告 `CComClassFactory` 做為預設的 Class Factory。  若要使用 `CComClassFactorySingleton`，請指定 [DECLARE\_CLASSFACTORY\_SINGLETON](../Topic/DECLARE_CLASSFACTORY_SINGLETON.md) 巨集在物件的類別定義。  例如：  
  
 [!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/CPP/ccomclassfactorysingleton-class_1.h)]  
  
## 繼承階層架構  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IClassFactory`  
  
 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md)  
  
 `CComClassFactorySingleton`  
  
## 需求  
 **Header:** atlcom.h  
  
## 請參閱  
 [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)   
 [CComClassFactory2 Class](../../atl/reference/ccomclassfactory2-class.md)   
 [CComClassFactoryAutoThread Class](../../atl/reference/ccomclassfactoryautothread-class.md)   
 [CComObjectRootEx Class](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](../Topic/CComGlobalsThreadModel.md)   
 [Class Overview](../../atl/atl-class-overview.md)