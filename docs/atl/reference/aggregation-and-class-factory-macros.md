---
title: "Aggregation and Class Factory Macros | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aggregation [C++], ATL macros"
  - "class factories, ATL macros"
ms.assetid: d99d379a-0eec-481f-8daa-252dac18f163
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# Aggregation and Class Factory Macros
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這些巨集的控制項模式和彙總宣告 Class Factory。  
  
|||  
|-|-|  
|[DECLARE\_AGGREGATABLE](../Topic/DECLARE_AGGREGATABLE.md)|宣告您的物件可彙總 \(預設值\)。|  
|[DECLARE\_CLASSFACTORY](../Topic/DECLARE_CLASSFACTORY.md)|宣告 Class Factory 是 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md)， ATL 預設 Class Factory。|  
|[DECLARE\_CLASSFACTORY\_EX](../Topic/DECLARE_CLASSFACTORY_EX.md)|宣告您的 Class Factory 物件是 Class Factory。|  
|[DECLARE\_ CLASSFACTORY2](../Topic/DECLARE_CLASSFACTORY2.md)|宣告 [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) 是 Class Factory。|  
|[DECLARE\_CLASSFACTORY\_AUTO\_THREAD](../Topic/DECLARE_CLASSFACTORY_AUTO_THREAD.md)|宣告 [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) 是 Class Factory。|  
|[DECLARE\_CLASSFACTORY\_SINGLETON](../Topic/DECLARE_CLASSFACTORY_SINGLETON.md)|宣告 [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md) 是 Class Factory。|  
|[DECLARE\_GET\_CONTROLLING\_UNKNOWN](../Topic/DECLARE_GET_CONTROLLING_UNKNOWN.md)|宣告虛擬 `GetControllingUnknown` 函式。|  
|[DECLARE\_NOT\_AGGREGATABLE](../Topic/DECLARE_NOT_AGGREGATABLE.md)|宣告您的物件無法彙總。|  
|[DECLARE\_ONLY\_AGGREGATABLE](../Topic/DECLARE_ONLY_AGGREGATABLE.md)|宣告必須彙總您自己的物件。|  
|[DECLARE\_POLY\_AGGREGATABLE](../Topic/DECLARE_POLY_AGGREGATABLE.md)|檢查的值的外部未知且宣告您的物件 aggregatable aggregatable，或不適當。|  
|[DECLARE\_PROTECT\_FINAL\_CONSTRUCT](../Topic/DECLARE_PROTECT_FINAL_CONSTRUCT.md)|保護外部物件遭刪除在內部物件建構期間。|  
|[DECLARE\_VIEW\_STATUS](../Topic/DECLARE_VIEW_STATUS.md)|指定 **VIEWSTATUS** 旗標加入容器。|  
  
## 請參閱  
 [Macros](../../atl/reference/atl-macros.md)