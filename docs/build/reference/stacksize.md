---
title: "STACKSIZE | Microsoft Docs"
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
  - "STACKSIZE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "STACKSIZE .def 檔案陳述式"
ms.assetid: 4d8c79bd-1cb4-4e4d-90f2-b5a7a4d20e7a
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# STACKSIZE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

以位元組設定堆疊的大小。  
  
```  
STACKSIZE reserve[,commit]  
```  
  
## 備註  
 設定堆疊的另一種方式是使用[堆疊配置](../../build/reference/stack-stack-allocations.md) \(\/STACK\) 選項。  如需 *reserve* 和 `commit` 引數的詳細資訊，請參閱有關該選項的文件。  
  
 這個選項對 DLL 沒有任何影響。  
  
## 請參閱  
 [模組定義陳述式的規則](../../build/reference/rules-for-module-definition-statements.md)