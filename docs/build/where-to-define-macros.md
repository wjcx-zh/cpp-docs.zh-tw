---
title: "定義巨集的位置 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "定義巨集"
  - "巨集, NMAKE"
  - "NMAKE 程式, 定義巨集"
ms.assetid: 0fc59ec5-5f58-4644-b7da-7b021f7001af
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 定義巨集的位置
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在命令列中、命令檔案、Makefile 或 Tools.ini 檔案中定義巨集。  
  
 在 Makefile 或 Tools.ini 檔案中，每一個巨集定義都要出現在不同的行中，並且不能以空格或定位字元開頭。  等號附近的空格或定位字元會予以忽略。  所有[字串字元](../build/defining-an-nmake-macro.md)都是常值，包括前後的引號和空白字元。  
  
 在命令列或命令檔案中，空格和定位字元會分隔引數，並且不能置於等號前後。  如果 `string` 有空白字元或定位字元，請將字串本身或整個巨集以雙引號 \(" "\) 括住。  
  
## 請參閱  
 [定義 NMAKE 巨集](../build/defining-an-nmake-macro.md)