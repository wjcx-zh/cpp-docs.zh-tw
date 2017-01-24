---
title: "目標 | Microsoft Docs"
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
  - "目標, 在 NMAKE 中指定"
ms.assetid: 826ee849-4278-4c6e-97c3-79a2b5fe6463
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 目標
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在相依性行中使用任何有效的檔名、目錄名稱，或[虛擬目標](../build/pseudotargets.md) \(Pseudotarget\)，指定一個或多個目標。  使用一個或多個空格或定位字元分隔多個目標。  目標不區分大小寫。  允許使用檔名做為路徑。  目標不可超過 256 個字元。  如果在冒號之前的目標為單一字元，請使用分隔空格，否則 NMAKE 會將字母冒號的組合解譯為磁碟指定元。  
  
## 您還想知道關於哪些方面的詳細資訊？  
 [虛擬目標](../build/pseudotargets.md)  
  
 [多重目標](../build/multiple-targets.md)  
  
 [累計相依性](../build/cumulative-dependencies.md)  
  
 [多重描述區塊中的目標](../build/targets-in-multiple-description-blocks.md)  
  
 [相依性的副作用](../build/dependency-side-effects.md)  
  
## 請參閱  
 [描述區塊](../build/description-blocks.md)