---
title: "位元欄位 | Microsoft Docs"
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
  - "bitfields"
ms.assetid: e9a1010d-1e1b-487f-9943-3c574e08f544
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 位元欄位
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

結構位元欄位限制在 64 位元以內，可以為 signed int、unsigned int、int64 或 unsigned int64 型別。  跨越型別界限的位元欄位會略過一些位元，將位元欄位對齊至下一個型別對齊。  例如，整數位元欄位不能跨越 32 位元界限。  
  
## 請參閱  
 [類型和儲存區](../build/types-and-storage.md)