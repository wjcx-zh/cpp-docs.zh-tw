---
title: "執行緒模型和關鍵區段類別 (ATL) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.atl.threads.models
dev_langs:
- C++
helpviewer_keywords:
- ATL, critical sections
- ATL, multithreading
- threading [ATL], models
- critical sections
ms.assetid: 759f05ef-6285-4be6-a2cc-78572dd75146
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1501fe4f761b9bc8775018d6566ceff5fb0aa477
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="threading-models-and-critical-sections-classes"></a>執行緒模型和關鍵區段類別
下列類別定義的執行緒模型和關鍵區段：  
  
-   [CAtlAutoThreadModule](../atl/reference/catlautothreadmodule-class.md)實作在集區執行緒的 apartment model COM 伺服器。  
  
-   [CAtlAutoThreadModuleT](../atl/reference/catlautothreadmodulet-class.md)提供方法來實作在集區執行緒的 apartment model COM 伺服器。  
  
-   [CComMultiThreadModel](../atl/reference/ccommultithreadmodel-class.md)遞增和遞減的變數提供安全執行緒的方法。 提供的重要區段。  
  
-   [CComMultiThreadModelNoCS](../atl/reference/ccommultithreadmodelnocs-class.md)遞增和遞減的變數提供安全執行緒的方法。 不提供重要區段。  
  
-   [CComSingleThreadModel](../atl/reference/ccomsinglethreadmodel-class.md)遞增和遞減的變數提供的方法。 不提供重要區段。  
  
-   [CComObjectThreadModel](../atl/reference/atl-typedefs.md#ccomobjectthreadmodel)決定適當的執行緒模型類別，為單一物件類別。  
  
-   [CComGlobalsThreadModel](../atl/reference/atl-typedefs.md#ccomglobalsthreadmodel)決定適當的執行緒模型類別的全域可用的物件。  
  
-   [CComAutoCriticalSection](../atl/reference/ccomautocriticalsection-class.md)包含方法取得和釋放重要區段。 自動初始化重要區段。  
  
-   [CComCriticalSection](../atl/reference/ccomcriticalsection-class.md)包含方法取得和釋放重要區段。 關鍵區段必須先明確初始化。  
  
-   [CComFakeCriticalSection](../atl/reference/ccomfakecriticalsection-class.md)鏡像處理中的方法`CComCriticalSection`而不需提供重要區段。 中的方法`CComFakeCriticalSection`不執行任何動作。  
  
-   [CRTThreadTraits](../atl/reference/crtthreadtraits-class.md)提供 CRT 執行緒建立函式。 如果執行緒會使用 CRT 函式，請使用這個類別。  
  
-   [Win32ThreadTraits](../atl/reference/win32threadtraits-class.md)提供 Windows 執行緒建立函式。 如果執行緒不會使用 CRT 函式，請使用這個類別。  
  
## <a name="see-also"></a>請參閱  
 [類別概觀](../atl/atl-class-overview.md)

