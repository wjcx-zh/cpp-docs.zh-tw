---
title: "/STACK | Microsoft Docs"
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
  - "/stack"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/STACK editbin 選項"
  - "STACK editbin 選項"
  - "-STACK editbin 選項"
  - "堆疊, 設定大小"
ms.assetid: a39bcff0-c945-4355-80cc-8e4f24a5f142
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /STACK
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/STACK:reserve[,commit]  
```  
  
## 備註  
 這個選項以位元組為單位設定堆疊大小，並接受以十進位數或 C 語言標記法表示的引數。  \/STACK 選項僅適用於可執行檔。  
  
 *reserve* 引數指定虛擬記憶體中的堆疊配置 \(Stack Allocation\) 總計。  EDITBIN 會將指定的值進位至最接近 4 的倍數個位元組。  
  
 選擇性 `commit` 引數是隨作業系統的解讀而異。  在 Windows NT、Windows 95 和 Windows 98 中，`commit` 指定一次要配置之實體記憶體量。  認可的虛擬記憶體會在分頁檔中保留空間。  當應用程式需要更多的堆疊空間時，較高的 `commit` 值可節省時間，但會增加記憶體需求且可能增加啟動時間。  
  
## 請參閱  
 [EDITBIN 選項](../../build/reference/editbin-options.md)