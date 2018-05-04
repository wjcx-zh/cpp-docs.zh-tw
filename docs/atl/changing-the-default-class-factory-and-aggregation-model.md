---
title: 變更預設 Class Factory 和彙總模型 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CComClassFactory class, making the default
- aggregation [C++], using ATL
- aggregation [C++], aggregation models
- defaults [C++], aggregation model in ATL
- default class factory
- class factories, changing default
- CComCoClass class, default class factory and aggregation model
- default class factory, ATL
- defaults [C++], class factory
ms.assetid: 6e040e95-0f38-4839-8a8b-c9800dd47e8c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ce64f2162aa0d5cdf5bcf5e16b56b6989fcaf1ee
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="changing-the-default-class-factory-and-aggregation-model"></a>變更預設 Class Factory 和彙總模型
使用 ATL [CComCoClass](../atl/reference/ccomcoclass-class.md)來定義物件的預設類別處理站和彙總模型。 `CComCoClass` 指定下列兩個巨集：  
  
-   [DECLARE_CLASSFACTORY](reference/aggregation-and-class-factory-macros.md#declare_classfactory)宣告 class factory 是[CComClassFactory](../atl/reference/ccomclassfactory-class.md)。  
  
-   [DECLARE_AGGREGATABLE](reference/aggregation-and-class-factory-macros.md#declare_aggregatable)宣告您的物件可以彙總。  
  
 您可以在類別定義中指定其他巨集來覆寫其中一個這些預設值設定。 例如，若要使用[CComClassFactory2](../atl/reference/ccomclassfactory2-class.md)而不是`CComClassFactory`，指定[DECLARE_CLASSFACTORY2](reference/aggregation-and-class-factory-macros.md#declare_classfactory2)巨集：  
  
 [!code-cpp[NVC_ATL_COM#2](../atl/codesnippet/cpp/changing-the-default-class-factory-and-aggregation-model_1.h)]  
  
 兩個其他定義的類別處理站的巨集[DECLARE_CLASSFACTORY_AUTO_THREAD](reference/aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread)和[DECLARE_CLASSFACTORY_SINGLETON](reference/aggregation-and-class-factory-macros.md#declare_classfactory_singleton)。  
  
 也會使用 ATL`typedef`機制來實作預設行為。 例如，`DECLARE_AGGREGATABLE`巨集使用`typedef`定義類型，稱為 **_CreatorClass**，然後參考整個 ATL 在衍生類別中，請注意，`typedef`使用相同名稱的基底類別`typedef`導致 ATL 使用您的定義，並覆寫預設行為。  
  
## <a name="see-also"></a>另請參閱  
 [ATL COM 物件的基本概念](../atl/fundamentals-of-atl-com-objects.md)   
 [彙總和 Class Factory 巨集](../atl/reference/aggregation-and-class-factory-macros.md)

