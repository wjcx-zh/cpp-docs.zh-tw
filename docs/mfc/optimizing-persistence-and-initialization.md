---
title: "最佳化持續性和初始化 | Microsoft Docs"
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
  - "MFC ActiveX 控制項, 最佳化"
  - "最佳化, ActiveX 控制項"
  - "最佳化效能, ActiveX 控制項"
  - "效能, ActiveX 控制項"
ms.assetid: e821e19e-b9eb-49ab-b719-0743420ba80b
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 最佳化持續性和初始化
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

根據預設，持續性和初始化在控制由 `DoPropExchange` 成員函式來處理。  在典型的控制項，這個函式包含呼叫數個 **PX\_** 函式 \(`PX_Color`， `PX_Font`，等等\)，而每個屬性的。  
  
 這種方法有好處單一 `DoPropExchange` 實作可用於初始化，以繼續以二進位格式並繼續在某些容器使用的所謂的屬性包」格式。  這個函式在方便位元提供屬性和其預設值的所有資訊。  
  
 不過，這普通性犧牲效率來。  **PX\_** 函式會比更直接原本效率的多層的實作，不過，較不具彈性的，方法會取得其彈性。  此外，否則，控制項會預設值為 **PX\_** 函式，即使在條件都必須在提供的預設值，當，可以不一定使用時的預設值。  如果產生的預設值是重要的工作 \(例如，，當值從環境屬性取得\)，則額外，不必要的工作已完成，在不使用的預設值。  
  
 您可以覆寫控制項的 `Serialize` 函式來改善控制項的二進位持續性效能。  此成員函式的預設實作會呼叫您的 `DoPropExchange` 函式。  您可以覆寫它，您可以為二進位持續性提供較簡單的實作。  例如，請考慮下列 `DoPropExchange` 函式:  
  
 [!code-cpp[NVC_MFC_AxOpt#1](../mfc/codesnippet/CPP/optimizing-persistence-and-initialization_1.cpp)]  
  
 若要改善這個控制項的二進位持續性效能，您可以覆寫 `Serialize` 函式:  
  
 [!code-cpp[NVC_MFC_AxOpt#2](../mfc/codesnippet/CPP/optimizing-persistence-and-initialization_2.cpp)]  
  
 `dwVersion` 區域變數可用來偵測的載入或儲存控制項的持續性狀態的版本。  您可以使用這個變數而不是呼叫 [CPropExchange::GetVersion](../Topic/CPropExchange::GetVersion.md)。  
  
 若要節省保存格式的點空間 **BOOL** 屬性 \(和保持它與 `PX_Bool`產生的格式相容\)，您可以將屬性視為 **BYTE**，如下所示:  
  
 [!code-cpp[NVC_MFC_AxOpt#3](../mfc/codesnippet/CPP/optimizing-persistence-and-initialization_3.cpp)]  
  
 請注意在負載的情況下，暫存變數使用然後其值是指定，而不是轉換 `m_boolProp` 對 **BYTE** 參考。  轉換製程只會被修改的位元組 `m_boolProp` ，保留其餘位元組未初始化。  
  
 對於相同的控制項，您可以覆寫 [COleControl::OnResetState](../Topic/COleControl::OnResetState.md) 最佳化控制項的初始化如下:  
  
 [!code-cpp[NVC_MFC_AxOpt#4](../mfc/codesnippet/CPP/optimizing-persistence-and-initialization_4.cpp)]  
  
 `Serialize` 和 `OnResetState` 同樣覆寫，應該保持 `DoPropExchange` 函式不變，因為它會繼續仍然使用在屬性包格式。  維護全部三個函式一定會是重要的控制項一致地管理其屬性，保存性機制的容器使用。  
  
## 請參閱  
 [MFC ActiveX 控制項：最佳化](../mfc/mfc-activex-controls-optimization.md)