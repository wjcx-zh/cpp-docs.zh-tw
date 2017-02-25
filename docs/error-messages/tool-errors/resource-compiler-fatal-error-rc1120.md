---
title: "資源編譯器嚴重錯誤 RC1120 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RC1120"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC1120"
ms.assetid: 4e462931-e42e-42e3-8bfc-847677194286
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 資源編譯器嚴重錯誤 RC1120
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

out of memory, needed number bytes  
  
 資源編譯器儲存在堆積 \(Heap\) 中項目的儲存體已用完。  這通常是由於具有過多的符號所引起。  
  
### 若要採用下列可能解決方式以進行修正  
  
1.  增加 Windows 交換檔 \(Swap File\) 空間。  如需增加交換檔空間的詳細資訊，請參閱 Windows 說明中的虛擬記憶體部分。  
  
2.  排除不必要的包含檔案，特別是不需要的 `#define` 以及函式原型 \(Prototype\)。  
  
3.  將目前的檔案分割成兩個以上的檔案，然後分別進行編譯。  
  
4.  將系統上正在執行的其他程式或驅動程式移除，因為這些程式可能會消耗大量的記憶體。