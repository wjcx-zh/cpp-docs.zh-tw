---
title: ".DOSSEG | Microsoft Docs"
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
  - ".DOSSEG"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".DOSSEG directive"
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .DOSSEG
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

排序依據以 MS\-DOS 的區段慣例區段： 程式碼第一次，然後區段不在 DGROUP，然後區段在 DGROUP 中。  
  
## 語法  
  
```  
  
.DOSSEG  
  
```  
  
## 備註  
 DGROUP 中的區段，請依照下列順序： 區段未在 BSS 或堆疊，然後 BSS 區段，並最後堆疊區段。  主要用於確保在 MASM 獨立程式的可檢視程式碼支援。  相同的 [DOSSEG](../../assembler/masm/dosseg.md)。  
  
## 請參閱  
 [Directives Reference](../../assembler/masm/directives-reference.md)