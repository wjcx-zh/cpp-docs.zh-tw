---
title: ATL 視窗特性 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- window traits
ms.assetid: c90cf850-9e91-49da-9cf3-ad4efb30347d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 91ea30c79712ced6c86da0b030882fe6a88359ed
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43764039"
---
# <a name="understanding-window-traits"></a>了解視窗特性

視窗 traits 類別提供簡單的方法標準化用於建立 ATL 視窗物件的樣式。 視窗特性都被視為由範本參數[CWindowImpl](../atl/reference/cwindowimpl-class.md)和其他 ATL 視窗類別，這種方式提供預設的視窗樣式，在類別層級。

如果視窗執行個體的建立者未提供明確的呼叫中的樣式[建立](../atl/reference/cwindowimpl-class.md#create)，您可以使用 traits 類別，以確保視窗仍會建立具有正確的樣式。 您甚至可以確定的特定樣式設為該視窗類別的所有執行個體同時允許其他樣式為設定每個執行個體為基礎。

## <a name="atl-window-traits-templates"></a>ATL 視窗特性範本

ATL 提供兩個視窗特性範本可讓您設定在編譯時期使用其樣板參數的預設樣式。

|類別|描述|
|-----------|-----------------|
|[CWinTraits](../atl/reference/cwintraits-class.md)|使用此範本，當您想要提供預設會在呼叫中不指定任何其他樣式時使用的視窗樣式`Create`。 提供在執行的階段優先順序，透過在設定樣式的樣式會編譯時間。|
|[CWinTraitsOR](../atl/reference/cwintraitsor-class.md)|當您想要指定必須一律設定為視窗類別的樣式，請使用這個類別。 在執行階段提供的樣式會結合以在使用位元的 OR 運算子的編譯時期設定樣式。|

除了這些範本，還會使用 ATL 提供數個預先定義的特製化`CWinTraits`常用的組合的視窗樣式的範本。 請參閱[CWinTraits](../atl/reference/cwintraits-class.md)參考文件的完整詳細資料。

## <a name="custom-window-traits"></a>自訂視窗特性

在不太可能的情況下，特製化其中一個提供的 ATL 範本不足夠且您需要建立您自己的 traits 類別，您只需要建立一個類別來實作兩個靜態函式：`GetWndStyle`和`GetWndStyleEx`:

[!code-cpp[NVC_ATL_Windowing#68](../atl/codesnippet/cpp/understanding-window-traits_1.h)]

所有這些函式會在執行階段，它可用來產生新的樣式值傳遞一些樣式值。 如果您的視窗 traits 類別做 ATL 視窗類別的樣板引數，傳遞至這些靜態函式的樣式值會傳遞做為樣式引數[建立](../atl/reference/cwindowimpl-class.md#create)。

## <a name="see-also"></a>另請參閱

[視窗類別](../atl/atl-window-classes.md)

