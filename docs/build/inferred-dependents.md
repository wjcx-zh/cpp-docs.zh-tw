---
title: "推斷相依 | Microsoft Docs"
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
  - "相依性, 推斷"
  - "NMAKE 中的推斷相依"
ms.assetid: 9303045c-69b3-4f35-bffc-19d5cd6ea3c3
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 推斷相依
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

推斷相依衍生自推斷規則，並在明確相依之前進行評估。  如果推斷相依相對於它自己的目標是過時的，NMAKE 就會叫用相依性的命令區塊。  如果推斷相依不存在，或相對於自身的相依性是過時的，NMAKE 會先更新推斷相依。  如需推斷相依的詳細資訊，請參閱[推斷規則](../build/inference-rules.md)。  
  
## 請參閱  
 [相依性](../build/dependents.md)