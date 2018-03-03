---
title: "最佳化持續性和初始化 |Microsoft 文件"
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
- MFC ActiveX controls [MFC], optimizing
- performance, ActiveX controls
- optimization, ActiveX controls
- optimizing performance, ActiveX controls
ms.assetid: e821e19e-b9eb-49ab-b719-0743420ba80b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eeddfe4c67de2e96d42c7714619463ae3be45187
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="optimizing-persistence-and-initialization"></a>最佳化持續性和初始化
根據預設，持續性和控制項中的初始化會由`DoPropExchange`成員函式。 在典型的控制項，此函式包含數個呼叫**PX_**函式 (`PX_Color`，`PX_Font`等等)，其中每一個屬性。  
  
 這種方法的優點是，單一`DoPropExchange`初始化、 持續性的二進位格式，以及所謂 「 屬性包"格式某些容器所使用的持續性，可以使用實作。 這一個函式提供屬性和其預設值在一個方便的位置中的所有資訊。  
  
 不過，這項通則的效率。 **PX_**函式取得多層次的實作，原本就較不透過彈性比更直接的但較有彈性方法有效率。 此外，如果控制權會傳遞至預設值**PX_**函式中，每次，即使在使用時，預設值可能不一定的情況下必須提供預設值。 如果產生的預設值是重要的工作 （例如，值取自環境的屬性時），則額外，不使用預設值的情況下會進行不必要的工作。  
  
 您可以藉由覆寫您的控制項來改善您的控制項二進位的持續性效能`Serialize`函式。 此成員函式的預設實作會呼叫您`DoPropExchange`函式。 藉由覆寫它，您可以提供二進位的持續性更直接的實作。 例如，請考慮下列事項`DoPropExchange`函式：  
  
 [!code-cpp[NVC_MFC_AxOpt#1](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_1.cpp)]  
  
 若要改善這個控制項的二進位持續性效能，您可以覆寫`Serialize`函式，如下所示：  
  
 [!code-cpp[NVC_MFC_AxOpt#2](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_2.cpp)]  
  
 `dwVersion`本機變數可以用來偵測要在載入或儲存控制項的永續性狀態的版本。 您可以使用這個變數，而不是呼叫[CPropExchange::GetVersion](../mfc/reference/cpropexchange-class.md#getversion)。  
  
 若要儲存極小空間中的持續性格式**BOOL**屬性 (並使其與所產生的格式相容`PX_Bool`)，您可以儲存屬性做為**位元組**、，如下所示：  
  
 [!code-cpp[NVC_MFC_AxOpt#3](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_3.cpp)]  
  
 請注意，在負載情況下，會使用暫存變數，則會指派它的值，而不是轉型`m_boolProp`至**位元組**參考。 轉型技術會導致只有一個位元組的`m_boolProp`遭到修改，但未初始化的剩餘的位元組會保留。  
  
 針對相同的控制項，您可以藉由覆寫最佳化控制項的初始化[COleControl::OnResetState](../mfc/reference/colecontrol-class.md#onresetstate) ，如下所示：  
  
 [!code-cpp[NVC_MFC_AxOpt#4](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_4.cpp)]  
  
 雖然`Serialize`和`OnResetState`已覆寫，`DoPropExchange`函式應該保持不變因為它仍會持續性的屬性包格式的使用。 請務必維護這三個不論哪一個持續性機制容器會使用這些函式以確保控制項以一致的方式，管理其屬性。  
  
## <a name="see-also"></a>請參閱  
 [MFC ActiveX 控制項：最佳化](../mfc/mfc-activex-controls-optimization.md)

