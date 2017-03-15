---
title: "在前置處理中執行程式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "程式執行 [C++]"
ms.assetid: 5ecf123a-20e5-40cd-b8d8-dd5a9fdd4b24
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 在前置處理中執行程式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要在前置處理中使用命令的結束代碼，請在括號 \(\[ \]\) 內指定命令以及任何引數。  在執行命令以前會先展開所有巨集。  NMAKE 以命令的結束代碼取代命令規格，此代碼可在運算式中用以控制前置處理。  
  
## 請參閱  
 [Makefile 前置處理中的運算式](../build/expressions-in-makefile-preprocessing.md)