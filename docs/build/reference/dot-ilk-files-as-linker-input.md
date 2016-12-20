---
title: ".Ilk 檔做為連結器輸入 | Microsoft Docs"
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
  - ".ilk 檔案"
  - "ILK 檔案"
ms.assetid: 7324c104-9e5d-423d-b268-b59f92607bf2
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .Ilk 檔做為連結器輸入
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在以累加方式連結時，LINK 會更新它在第一次累加連結時所建立的 .ilk 狀態檔。  這個檔案與 .exe 檔或 .dll 檔具有相同的主檔名 \(Base Name\)，不過它的副檔名為 .ilk。  在後續的累加連結期間，LINK 會持續更新這個 .ilk 檔。  如果 .ilk 檔遺失了，LINK 便會執行完整的連結並且建立一個新的 .ilk 檔。  如果 .ilk 檔無法使用，LINK 會執行非累加連結。  如需有關累加連結的詳細資訊，請參閱[以累加方式連結 \(\/INCREMENTAL\)](../../build/reference/incremental-link-incrementally.md) 選項。  
  
## 請參閱  
 [LINK 輸入檔](../../build/reference/link-input-files.md)   
 [連結器選項](../../build/reference/linker-options.md)