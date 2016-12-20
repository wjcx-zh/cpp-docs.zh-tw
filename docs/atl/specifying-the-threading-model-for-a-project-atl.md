---
title: "指定專案的執行緒模型 (ATL) | Microsoft Docs"
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
  - "_ATL_APARTMENT_THREADED 巨集"
  - "_ATL_FREE_THREADED 巨集"
  - "_ATL_SINGLE_THREADED 巨集"
  - "ATL, 多執行緒"
  - "執行緒 [ATL], 模型"
ms.assetid: 6b571078-521c-4f3e-9f08-482aa235a822
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 指定專案的執行緒模型 (ATL)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列巨集可指定 ATL 專案的執行緒模型:  
  
|巨集|使用指南。|  
|--------|-----------|  
|\_ATL\_SINGLE\_THREADED|如果您所有的物件使用單一執行緒模型，請定義。|  
|\_ATL\_APARTMENT\_THREADED|如果第一個或更多的物件使用 Apartment 執行緒，請定義。|  
|\_ATL\_FREE\_THREADED|如果第一個或更多的物件使用中性或無限制執行緒，請定義。  現有的程式碼可能包含對等於 [\_ATL\_MULTI\_THREADED](../Topic/_ATL_MULTI_THREADED.md)巨集的參考。|  
  
 如果您沒有定義專案的這些巨集的任何一個， \_ATL\_FREE\_THREADED 實際上就是。  
  
 巨集來影響執行階段效能如下所示:  
  
-   指定對應至您的專案物件的巨集的執行階段效能。  
  
-   指定的巨集，例如，如果指定 \_ATL\_APARTMENT\_THREADED，當您所有的物件都是單一執行緒，會有些微降低執行階段效能。  
  
-   指定巨集，較低層級，例如，如果您指定 \_ATL\_SINGLE\_THREADED，將一或多個您的物件使用 Apartment 執行緒或無限制執行緒時，可能會讓應用程式在執行階段。  
  
 提供執行緒模型的說明請參閱 [選取， ATL 簡單物件精靈](../atl/reference/options-atl-simple-object-wizard.md) 可用的 ATL 物件。  
  
## 請參閱  
 [概念](../atl/active-template-library-atl-concepts.md)