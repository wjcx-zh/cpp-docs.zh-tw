---
title: "Threading Models and Critical Sections Classes | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.atl.threads.models"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, critical sections"
  - "ATL, 多執行緒"
  - "critical sections"
  - "執行緒 [ATL], 模型"
ms.assetid: 759f05ef-6285-4be6-a2cc-78572dd75146
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Threading Models and Critical Sections Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列類別會定義一個執行緒模型和關鍵區段:  
  
-   [CAtlAutoThreadModule](../atl/reference/catlautothreadmodule-class.md) 實作執行緒集區， Apartment Model COM 伺服器。  
  
-   [CAtlAutoThreadModuleT](../atl/reference/catlautothreadmodulet-class.md) 用於實作執行緒集區提供了方法， Apartment Model COM 伺服器。  
  
-   [CComMultiThreadModel](../atl/reference/ccommultithreadmodel-class.md) 為遞增和遞減變數提供執行緒安全的方法。  提供關鍵區段。  
  
-   [CComMultiThreadModelNoCS](../atl/reference/ccommultithreadmodelnocs-class.md) 為遞增和遞減變數提供執行緒安全的方法。  不提供關鍵區段。  
  
-   [CComSingleThreadModel](../atl/reference/ccomsinglethreadmodel-class.md) 為遞增和遞減變數的方法。  不提供關鍵區段。  
  
-   [CComObjectThreadModel](../Topic/CComObjectThreadModel.md) 決定單一物件類別的適當的執行緒模型類別。  
  
-   [CComGlobalsThreadModel](../Topic/CComGlobalsThreadModel.md) 判斷是全域可用物件的適當的執行緒模型類別。  
  
-   [CComAutoCriticalSection](../atl/reference/ccomautocriticalsection-class.md) 包含取得和釋放的關鍵區段 \(Critical Section\) 方法。  這個關鍵區段執行。會自動初始化。  
  
-   [CComCriticalSection](../atl/reference/ccomcriticalsection-class.md) 包含取得和釋放的關鍵區段 \(Critical Section\) 方法。  必須明確初始化關鍵區段。  
  
-   [CComFakeCriticalSection](../atl/reference/ccomfakecriticalsection-class.md) 反映在 `CComCriticalSection` 的方法，但不提供關鍵區段。  在 `CComFakeCriticalSection` 的方法不會有任何作用。  
  
-   [CRTThreadTraits](../atl/reference/crtthreadtraits-class.md) CRT 針對執行緒提供建立函式。  如果執行緒是使用 CRT 函式，請使用這個類別。  
  
-   [Win32ThreadTraits](../atl/reference/win32threadtraits-class.md) 為 Windows 執行緒提供建立函式。  如果執行緒不會使用 CRT 函式，請使用這個類別。  
  
## 請參閱  
 [Class Overview](../atl/atl-class-overview.md)