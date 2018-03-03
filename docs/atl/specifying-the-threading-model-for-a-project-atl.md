---
title: "指定執行緒模型專案 (ATL) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- _ATL_FREE_THREADED macro
- _ATL_APARTMENT_THREADED macro
- ATL, multithreading
- threading [ATL], models
- _ATL_SINGLE_THREADED macro
ms.assetid: 6b571078-521c-4f3e-9f08-482aa235a822
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a4c115b326d2cdfe82a0466461bd378fd1b4be80
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="specifying-the-threading-model-for-a-project-atl"></a>指定專案的執行緒模型 (ATL)
下列巨集，可用來指定執行緒模型的 ATL 專案：  
  
|巨集|使用的指導方針|  
|-----------|--------------------------|  
|_ATL_SINGLE_THREADED|如果所有物件都使用單一執行緒模型，定義。|  
|_ATL_APARTMENT_THREADED|如果一或多個物件使用 apartment 執行緒，定義。|  
|_ATL_FREE_THREADED|如果一或多個物件會使用執行緒可用或中性，定義。 現有的程式碼可能會包含參考的對等的巨集[_ATL_MULTI_THREADED](reference/compiler-options-macros.md#_atl_multi_threaded)。|  
  
 如果您沒有定義任何這些巨集的專案，_ATL_FREE_THREADED 將會生效。  
  
 巨集會影響執行階段效能，如下所示：  
  
-   指定的巨集對應至您的專案中的物件，可以改善執行階段效能。  
  
-   指定較高等級的巨集，例如，如果您指定 _ATL_APARTMENT_THREADED 時所有物件都是單一執行緒，將會稍微降低執行階段效能。  
  
-   指定的巨集，例如，較低層級，如果您指定 _ATL_SINGLE_THREADED 當一或多個物件使用 apartment 執行緒或無限制執行緒，會導致您的應用程式在執行階段失敗。  
  
 請參閱[選項，ATL 簡單物件精靈](../atl/reference/options-atl-simple-object-wizard.md)的描述就會忽略執行緒模型 ATL 物件可用的。  
  
## <a name="see-also"></a>請參閱  
 [概念](../atl/active-template-library-atl-concepts.md)

