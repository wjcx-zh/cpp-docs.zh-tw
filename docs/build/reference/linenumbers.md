---
title: "/LINENUMBERS | Microsoft Docs"
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
  - "/linenumbers"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/LINENUMBERS dumpbin 選項"
  - "行號"
  - "LINENUMBERS dumpbin 選項"
  - "-LINENUMBERS dumpbin 選項"
ms.assetid: 1681d582-2c2f-484e-9920-109959549055
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /LINENUMBERS
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/LINENUMBERS  
```  
  
## 備註  
 這個選項會顯示 COFF 行號。  如果以 \[程式資料庫 \(\/Zi\)\]、\[C7 相容 \(\/Z7\)\] 或 \[僅行數 \(\/Zd\)\] 編譯，行號會存在於目的檔中。  如果可執行檔或 DLL 使用 \[產生偵錯資訊 \(\/DEBUG\)\] 連結，檔案將會包含 COFF 行號。  
  
 只有 [\/HEADERS](../../build/reference/headers.md) DUMPBIN 選項可用在以 [\/GL](../../build/reference/gl-whole-program-optimization.md) 編譯器選項所產生的檔案上。  
  
## 請參閱  
 [DUMPBIN 選項](../../build/reference/dumpbin-options.md)