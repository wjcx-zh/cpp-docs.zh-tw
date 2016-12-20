---
title: "Controls: General Support Classes | Microsoft Docs"
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
  - "vc.atl.controls"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "控制項 [ATL]"
  - "general support classes"
ms.assetid: cf73f1d2-7542-48e3-b8c8-9d3abf29f85b
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Controls: General Support Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列類別會提供 ATL 控制項提供一般支援:  
  
-   [CComControl](../atl/reference/ccomcontrol-class.md) 包括 Helper ATL 控制項是基本函式和資料成員。  
  
-   [IOleControlImpl](../atl/reference/iolecontrolimpl-class.md) 提供方法所需的控制項。  
  
-   [IOleObjectImpl](../atl/reference/ioleobjectimpl-class.md) 提供容器與控制項溝通的主要方法。  處理控制項的就地啟動和停用。  
  
-   [IQuickActivateImpl](../atl/reference/iquickactivateimpl-class.md) 組合初始化為協助容器的單一呼叫中避免延遲，當載入控制項。  
  
-   [IPointerInactiveImpl](../atl/reference/ipointerinactiveimpl-class.md) 為則為非現用控制項提供最少的滑鼠互動。  
  
## 範例程式。  
 [ATLFire](../top/visual-cpp-samples.md)  
  
## 相關文件  
 [ATL 教學課程](../atl/active-template-library-atl-tutorial.md)  
  
## 請參閱  
 [Class Overview](../atl/atl-class-overview.md)