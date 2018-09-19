---
title: 變更預設 Class Factory 和彙總模型 |Microsoft Docs
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
ms.openlocfilehash: 203aeae7dd2edb179ec3f9c1f56f989ffc09b35c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093008"
---
# <a name="changing-the-default-class-factory-and-aggregation-model"></a>變更預設 Class Factory 和彙總模型

使用 ATL [CComCoClass](../atl/reference/ccomcoclass-class.md)來定義物件的預設類別處理站和彙總模型。 `CComCoClass` 指定下列兩個巨集：

- [DECLARE_CLASSFACTORY](reference/aggregation-and-class-factory-macros.md#declare_classfactory)宣告為的 class factory [CComClassFactory](../atl/reference/ccomclassfactory-class.md)。

- [DECLARE_AGGREGATABLE](reference/aggregation-and-class-factory-macros.md#declare_aggregatable)宣告您的物件可加以彙總。

您可以藉由在您的類別定義中指定另一個巨集來覆寫這些預設值的其中一個設定。 例如，若要使用[CComClassFactory2](../atl/reference/ccomclassfactory2-class.md)而不是`CComClassFactory`，指定[DECLARE_CLASSFACTORY2](reference/aggregation-and-class-factory-macros.md#declare_classfactory2)巨集：

[!code-cpp[NVC_ATL_COM#2](../atl/codesnippet/cpp/changing-the-default-class-factory-and-aggregation-model_1.h)]

兩個其他定義 class factory 的巨集[DECLARE_CLASSFACTORY_AUTO_THREAD](reference/aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread)並[DECLARE_CLASSFACTORY_SINGLETON](reference/aggregation-and-class-factory-macros.md#declare_classfactory_singleton)。

也會使用 ATL **typedef**機制來實作預設行為。 DECLARE_AGGREGATABLE 巨集的使用，例如**typedef**定義類型，稱為`_CreatorClass`，這在整個 ATL 參考 請注意，在衍生類別中， **typedef**使用相同名稱的基底類別**typedef**導致 ATL，使用您的定義，並覆寫預設行為。

## <a name="see-also"></a>另請參閱

[ATL COM 物件的基本概念](../atl/fundamentals-of-atl-com-objects.md)<br/>
[彙總和 Class Factory 巨集](../atl/reference/aggregation-and-class-factory-macros.md)

