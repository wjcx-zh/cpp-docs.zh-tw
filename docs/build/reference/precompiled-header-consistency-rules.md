---
title: "先行編譯標頭的一致性規則 | Microsoft Docs"
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
  - "先行編譯標頭檔, 一致性原則"
ms.assetid: 844b1a14-5b0b-4276-a1f5-cc62f13f6dda
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 先行編譯標頭的一致性規則
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本章節將對協助您更有效使用先行編譯標頭的方針進行說明：  
  
-   [針對每個檔案使用的先行編譯標頭的一致性規則](../../build/reference/consistency-rules-for-per-file-use-of-precompiled-headers.md)  
  
-   [\/Yc 和 \/Yu 的一致性規則](../../build/reference/consistency-rules-for-yc-and-yu.md)  
  
 由於 PCH 檔案包含有關電腦環境以及有關程式的記憶體位址等資訊，因此您只能在建立 PCH 檔的電腦上使用該 PCH 檔。  
  
## 請參閱  
 [建立先行編譯標頭檔](../../build/reference/creating-precompiled-header-files.md)