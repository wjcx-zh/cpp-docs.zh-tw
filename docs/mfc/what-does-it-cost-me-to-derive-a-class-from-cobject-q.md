---
title: "從 CObject 衍生類別的成本多高？ | Microsoft Docs"
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
  - "CObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CObject 類別, 衍生類別的額外負荷"
ms.assetid: 9b92c98b-b3dd-48a7-9d24-c3b8554edf90
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 從 CObject 衍生類別的成本多高？
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在衍生的額外負荷從 [CObject](../mfc/reference/cobject-class.md) 類別是最小。  您的衍生類別只能繼承自四個虛擬函式和一個 [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) 物件。  
  
## 請參閱  
 [CObject 類別：常見問題集](../mfc/cobject-class-frequently-asked-questions.md)