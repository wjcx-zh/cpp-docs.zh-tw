---
title: "alloca | Microsoft Docs"
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
ms.assetid: 2b209335-e3a0-4934-93f0-3b5925d22918
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# alloca
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[\_alloca](../c-runtime-library/reference/alloca.md) 必須使用 16 位元組對齊方式，並且還必須使用框架指標。  
  
 已配置的堆疊必須在其下方加入空間，以供後續呼叫之函式的參數使用，如[堆疊配置](../build/stack-allocation.md)所述。  
  
## 請參閱  
 [堆疊使用方式](../build/stack-usage.md)