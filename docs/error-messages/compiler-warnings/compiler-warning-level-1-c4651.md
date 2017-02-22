---
title: "編譯器警告 (層級 1) C4651 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4651"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4651"
ms.assetid: f1ea82aa-4dc1-4972-b55a-57fdb962f0dd
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器警告 (層級 1) C4651
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定 'definition' 給先行編譯標頭檔，但不是針對目前的編譯  
  
 在產生先行編譯標頭時已經指定定義，但不是在本次編譯 \(Compilation\) 中。  
  
 該定義在先行編譯標頭中會生效，但是在其他程式碼中不會。  
  
 如果先行編譯標頭是以 \/DSYMBOL 建置，編譯器就會在 \/Yu 編譯沒有 \/DSYMBOL 時產生這項警告。加入 \/DSYMBOL 至 \/Yu 命令列，就能解除這項警告。