---
title: "類型程式庫存取 | Microsoft Docs"
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
  - "vc.mfc.macros"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "類型程式庫, 存取"
ms.assetid: a03fa7f0-86c2-4119-bf81-202916fb74b3
caps.latest.revision: 14
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 類型程式庫存取
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

型別程式庫公開 OLE automation 控制項的介面在其他 OLE 感知應用程式。  如果一或多個介面會公開，每個 OLE automation 控制項必須有型別程式庫。  
  
 下列巨集的 OLE automation 控制項提供對其型別程式庫:  
  
### 類型程式庫存取  
  
|||  
|-|-|  
|[DECLARE\_OLETYPELIB](../Topic/DECLARE_OLETYPELIB.md)|宣告 OLE automation 控制項的 `GetTypeLib` 成員函式 \(必須在類別宣告\)。|  
|[IMPLEMENT\_OLETYPELIB](../Topic/IMPLEMENT_OLETYPELIB.md)|實作 OLE automation 控制項的 `GetTypeLib` 成員函式 \(必須使用類別實作\)。|  
  
## 請參閱  
 [巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)