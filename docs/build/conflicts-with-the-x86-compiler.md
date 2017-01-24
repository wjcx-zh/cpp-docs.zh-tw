---
title: "與 x86 編譯器衝突 | Microsoft Docs"
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
ms.assetid: 8e47f0d3-afe0-42d9-9efa-de239ddd3a05
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 與 x86 編譯器衝突
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您使用 x 86 編譯器來編譯應用程式時，大於 4 個位元組的資料型別都不會在堆疊上自動對齊。  因為 x 86 編譯器的架構是 4 個位元組對齊的堆疊，大於 4 個位元組的任何項目，例如 64 位元整數，都無法自動對齊至 8 位元組地址。  
  
 處理未對齊的資料會有兩種影響。  
  
-   與存取已對齊的位置相較之下，存取未對齊的位置可能需要較長時間。  
  
-   在連鎖作業中不能使用未對齊的位置。  
  
 如果您需要更嚴格的對齊方式，請使用 `__declspec(align(N)) on your variable declarations`。  這會讓編譯器以動態方式對齊堆疊，以符合您的規格。  然而，以動態方式在執行階段調整堆疊，可能會使應用程式的執行減慢。  
  
## 請參閱  
 [類型和儲存區](../build/types-and-storage.md)   
 [align](../cpp/align-cpp.md)