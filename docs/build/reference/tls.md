---
title: "/TLS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/TLS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/TLS dumpbin 選項"
  - "-TLS dumpbin 選項"
ms.assetid: 2b3f48f9-cac4-4351-b15c-2833b43bc709
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# /TLS
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

顯示可執行檔的 IMAGE\_TLS\_DIRECTORY 結構。  
  
## 備註  
 \/TLS 會顯示 TLS 結構的欄位以及 TLS 回呼函式的位址。  
  
 如果程式不使用執行緒區域儲存區 \(Thread Local Storage\)，它的影像將不會包含 TLS 結構。如需詳細資訊，請參閱[執行緒](../../cpp/thread.md)。  
  
 IMAGE\_TLS\_DIRECTORY 是定義在 winnt.h 之內。  
  
## 請參閱  
 [DUMPBIN 選項](../../build/reference/dumpbin-options.md)