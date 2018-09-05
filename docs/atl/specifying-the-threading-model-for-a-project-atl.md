---
title: 指定的執行緒模型專案 (ATL) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- _ATL_FREE_THREADED macro
- _ATL_APARTMENT_THREADED macro
- ATL, multithreading
- threading [ATL], models
- _ATL_SINGLE_THREADED macro
ms.assetid: 6b571078-521c-4f3e-9f08-482aa235a822
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f8a37a3ec730b727f6e214aafad1a4acc65b1dc3
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43760025"
---
# <a name="specifying-the-threading-model-for-a-project-atl"></a>指定專案的執行緒模型 (ATL)

下列巨集可用於指定 ATL 專案的執行緒模型：

|巨集|使用指導方針|
|-----------|--------------------------|
|_ATL_SINGLE_THREADED|如果所有物件都使用單一執行緒模型，定義。|
|_ATL_APARTMENT_THREADED|定義一或多個物件使用 apartment 執行緒。|
|_ATL_FREE_THREADED|如果一或多個物件使用免費或中性執行緒，定義。 現有的程式碼可能會包含參考的對等的巨集中[_ATL_MULTI_THREADED](reference/compiler-options-macros.md#_atl_multi_threaded)。|

如果您沒有定義任何這些巨集的專案，_ATL_FREE_THREADED 將會生效。

巨集會影響執行階段效能，如下所示：

- 指定的巨集對應至您的專案中的物件，可以改善執行階段效能。

- 指定較高層級的巨集，例如，如果您指定 _ATL_APARTMENT_THREADED 時所有的物件都是單一執行緒，將會稍微降低執行階段效能。

- 指定的巨集，例如，較低層級，如果您指定 _ATL_SINGLE_THREADED 當一或多個您物件使用 apartment 執行緒或無限制執行緒，可能會導致您的應用程式在執行階段失敗。

請參閱[選項，ATL 簡單物件精靈](../atl/reference/options-atl-simple-object-wizard.md)的執行緒說明模型 ATL 物件。

## <a name="see-also"></a>另請參閱

[概念](../atl/active-template-library-atl-concepts.md)

