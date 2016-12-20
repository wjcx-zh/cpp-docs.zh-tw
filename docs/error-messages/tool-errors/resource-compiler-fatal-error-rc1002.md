---
title: "資源編譯器嚴重錯誤 RC1002 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RC1002"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC1002"
ms.assetid: b43dfece-0dc3-4d0b-9d8f-509699b9ae80
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 資源編譯器嚴重錯誤 RC1002
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

堆積空間不足  
  
### 若要採用下列可能解決方式以進行修正  
  
1.  增加 Windows 交換檔 \(Swap File\) 空間。  如需增加交換檔空間的詳細資訊，請參閱 Windows 說明中的虛擬記憶體部分。  
  
2.  將目前的檔案分割成幾個較小的檔案，然後分別進行編譯。  
  
3.  將系統上正在執行的其他程式或驅動程式移除。