---
title: "推斷相依和規則 | Microsoft Docs"
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
  - "NMAKE 中的推斷規則"
  - "規則, 推斷"
ms.assetid: 9381e74a-53d9-445c-836d-0ff7ef6112d9
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 推斷相依和規則
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果適用的推斷規則存在，NMAKE 就會假設目標的推斷相依。  規則將適用，若：  
  
-   *toext* 符合目標的副檔名。  
  
-   *fromext* 與有目標之主檔名，且存在於目前或指定目錄中的檔案之副檔名相符。  
  
-   *fromext* 位於 [.SUFFIXES](../build/dot-directives.md)；在相符的規則中沒有其他 *fromext* 擁有更高的 **.SUFFIXES** 優先權。  
  
-   沒有擁有更高 **.SUFFIXES** 優先權的明確相依。  
  
 推斷相依會造成未預期的副作用。  如果目標的描述區塊含有命令，NMAKE 會執行這些命令，而不是規則中的命令。  
  
## 請參閱  
 [推斷規則](../build/inference-rules.md)