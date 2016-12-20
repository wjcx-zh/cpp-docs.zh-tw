---
title: "Null 和未定義的巨集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "巨集, Null 和未定義"
  - "NMAKE 程式, Null 巨集"
  - "NMAKE 程式, 未定義的巨集"
  - "NMAKE 中的 Null 巨集"
  - "undefined 巨集與 NMAKE"
ms.assetid: 1db4611a-1755-4328-b00f-d35365af8b6c
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Null 和未定義的巨集
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

null 和未定義的巨集同時展開為 null 字串，但定義成 null 字串的巨集會被視為在前置處理中定義。  若要將巨集定義為 null 字串，在命令列或命令檔案中的等號 \(\=\) 後面，除了空格或定位字元以外，請不要指定字元，並將 null 字串或定義放置在雙引號 \(" "\) 內。  若要未定義巨集，請使用 **\!UNDEF**。如需詳細資訊，請參閱 [Makefile 前置處理指示詞](../build/makefile-preprocessing-directives.md)。  
  
## 請參閱  
 [定義 NMAKE 巨集](../build/defining-an-nmake-macro.md)