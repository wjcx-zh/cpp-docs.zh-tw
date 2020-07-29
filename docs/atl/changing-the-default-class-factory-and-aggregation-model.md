---
title: 變更預設的 Class Factory 和匯總模型
ms.date: 11/04/2016
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
ms.openlocfilehash: 1c97d8f63a441fab2b76c6e0509e4b3f384308ea
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220882"
---
# <a name="changing-the-default-class-factory-and-aggregation-model"></a>變更預設的 Class Factory 和匯總模型

ATL 會使用[CComCoClass](../atl/reference/ccomcoclass-class.md)來定義物件的預設 Class Factory 和匯總模型。 `CComCoClass`指定下列兩個宏：

- [DECLARE_CLASSFACTORY](reference/aggregation-and-class-factory-macros.md#declare_classfactory)宣告要[CComClassFactory](../atl/reference/ccomclassfactory-class.md)的 Class Factory。

- [DECLARE_AGGREGATABLE](reference/aggregation-and-class-factory-macros.md#declare_aggregatable)宣告您的物件可以匯總。

您可以藉由在類別定義中指定另一個宏，覆寫其中一個預設值。 例如，若要使用[CComClassFactory2](../atl/reference/ccomclassfactory2-class.md)而不是 `CComClassFactory` ，請指定[DECLARE_CLASSFACTORY2](reference/aggregation-and-class-factory-macros.md#declare_classfactory2)宏：

[!code-cpp[NVC_ATL_COM#2](../atl/codesnippet/cpp/changing-the-default-class-factory-and-aggregation-model_1.h)]

定義 Class Factory 的兩個其他宏[DECLARE_CLASSFACTORY_AUTO_THREAD](reference/aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread)和[DECLARE_CLASSFACTORY_SINGLETON](reference/aggregation-and-class-factory-macros.md#declare_classfactory_singleton)。

ATL 也會使用 **`typedef`** 機制來執行預設行為。 例如，DECLARE_AGGREGATABLE 宏 **`typedef`** 會使用來定義名為的型別 `_CreatorClass` ，然後在整個 ATL 中參考它。 請注意，在衍生類別中， **`typedef`** 使用與基類相同的名稱，會 **`typedef`** 在 ATL 中使用您的定義並覆寫預設行為。

## <a name="see-also"></a>另請參閱

[ATL COM 物件的基本概念](../atl/fundamentals-of-atl-com-objects.md)<br/>
[匯總和類別 Factory 宏](../atl/reference/aggregation-and-class-factory-macros.md)
