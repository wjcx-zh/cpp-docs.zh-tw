---
title: "編譯器警告 (層級 1) C4325 | Microsoft Docs"
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
  - "C4325"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4325"
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4325
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**已忽略標準區段 '**   
 ***section* ' 的屬性**  
  
 您無法變更標準區段的屬性。  例如：  
  
```  
#pragma section(".sdata", long)  
```  
  
 這樣會以 **long** 資料型別覆寫使用 **short** 資料型別的 `.sdata` 標準區段。  
  
 您無法變更屬性的標準區段包括  
  
-   .data  
  
-   .sdata  
  
-   .bss  
  
-   .sbss  
  
-   .text  
  
-   .const  
  
-   .sconst  
  
-   .rdata  
  
-   .srdata  
  
 日後可能會加入其他區段。  
  
## 請參閱  
 [section](../../preprocessor/section.md)