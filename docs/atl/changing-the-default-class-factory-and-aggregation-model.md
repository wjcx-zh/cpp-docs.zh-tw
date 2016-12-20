---
title: "Changing the Default Class Factory and Aggregation Model | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aggregation [C++], aggregation models"
  - "aggregation [C++], 使用 ATL"
  - "CComClassFactory class, making the default"
  - "CComCoClass class, default class factory and aggregation model"
  - "class factories, 變更預設值"
  - "default class factory"
  - "default class factory, ATL"
  - "預設值 [C++], aggregation model in ATL"
  - "預設值 [C++], class factory"
ms.assetid: 6e040e95-0f38-4839-8a8b-c9800dd47e8c
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Changing the Default Class Factory and Aggregation Model
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用 ATL [CComCoClass](../atl/reference/ccomcoclass-class.md) 定義預設 Class Factory 和您的物件模型中的彙總。  `CComCoClass` 指定下列兩個巨集:  
  
-   [DECLARE\_CLASSFACTORY](../Topic/DECLARE_CLASSFACTORY.md) 宣告 Class Factory 是 [CComClassFactory](../atl/reference/ccomclassfactory-class.md)。  
  
-   [DECLARE\_AGGREGATABLE](../Topic/DECLARE_AGGREGATABLE.md) 宣告您的物件可彙總。  
  
 您可以指定另一個巨集覆寫這些預設值是在您的類別定義。  例如，使用 [CComClassFactory2](../atl/reference/ccomclassfactory2-class.md) 而不是 `CComClassFactory`，請指定 [DECLARE\_ CLASSFACTORY2](../Topic/DECLARE_CLASSFACTORY2.md) 巨集:  
  
 [!code-cpp[NVC_ATL_COM#2](../atl/codesnippet/CPP/changing-the-default-class-factory-and-aggregation-model_1.h)]  
  
 定義 Class Factory 的其他兩個巨集就 [DECLARE\_CLASSFACTORY\_AUTO\_THREAD](../Topic/DECLARE_CLASSFACTORY_AUTO_THREAD.md) 和 [DECLARE\_CLASSFACTORY\_SINGLETON](../Topic/DECLARE_CLASSFACTORY_SINGLETON.md)。  
  
 ATL 也使用 `typedef` 機制實作預設行為。  例如， `DECLARE_AGGREGATABLE` 巨集使用 `typedef` 定義呼叫 **\_CreatorClass**的型別，然後參考在 ATL 中。  請注意在衍生類別中，請使用名稱 `typedef` 和 ATL 中的基底類別 \(Base Class\) 的 `typedef` 結果相同使用您的定義以及覆寫預設行為。  
  
## 請參閱  
 [Fundamentals of ATL COM Objects](../atl/fundamentals-of-atl-com-objects.md)   
 [Aggregation and Class Factory Macros](../atl/reference/aggregation-and-class-factory-macros.md)