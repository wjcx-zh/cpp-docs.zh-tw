---
title: "/RANGE | Microsoft Docs"
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
  - "/RANGE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/RANGE dumpbin 選項"
  - "-RANGE dumpbin 選項"
ms.assetid: 7eeba266-32be-49cc-a350-96bdf541f98a
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /RANGE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

配合其他 dumpbin 選項 \(例如 \/RAWDATA 或 \/DISASM\) 使用時，修改 dumpbin 的輸出。  
  
## 語法  
  
```  
/RANGE:vaMin[,vaMax]  
```  
  
## 旗標  
 **vaMin**  
 您要 dumpbin 作業開始的虛擬位址。  
  
 **vaMax** \(選擇性\)  
 您要 dumpbin 作業結束的虛擬位址。  若未指定，則 dumpbin 會一直持續到檔案的結尾。  
  
## 備註  
 若要查看影像的虛擬位址，請使用影像的對應檔 \(RVA \+ Base\)、dumpbin 的**\/DISASM** 或 **\/HEADERS** 選項，或 Visual Studio 偵錯工具的反組譯碼視窗。  
  
## 範例  
 在本範例中是使用 **\/range** 修改 **\/disasm** 選項的顯示。  在本範例中，開始值是以十進位數表示，而結束值是以十六進位數指定。  
  
```  
dumpbin /disasm /range:4219334,0x004061CD t.exe  
```  
  
## 請參閱  
 [DUMPBIN 選項](../../build/reference/dumpbin-options.md)