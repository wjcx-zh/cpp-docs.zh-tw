---
title: "/LINKERMEMBER | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/linkermember"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/LINKERMEMBER dumpbin 選項"
  - "LINKERMEMBER dumpbin 選項"
  - "-LINKERMEMBER dumpbin 選項"
ms.assetid: c96868c1-d70e-4651-ae36-c55b58b16406
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /LINKERMEMBER
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/LINKERMEMBER[:{1|2}]  
```  
  
## 備註  
 這個選項顯示定義於程式庫的公用符號。  指定引數 1 時，可以物件順序顯示符號與其位移 \(Offset\)。  指定引數 2 時，可顯示物件的位移和索引編號，然後按英文字母順序列出符號以及各個符號的物件索引。  若要顯示這兩項輸出，請指定不帶數字引數的 \/LINKERMEMBER。  
  
 只有 [\/HEADERS](../../build/reference/headers.md) DUMPBIN 選項可用在以 [\/GL](../../build/reference/gl-whole-program-optimization.md) 編譯器選項所產生的檔案上。  
  
## 請參閱  
 [DUMPBIN 選項](../../build/reference/dumpbin-options.md)