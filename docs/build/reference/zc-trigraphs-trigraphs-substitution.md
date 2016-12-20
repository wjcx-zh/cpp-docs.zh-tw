---
title: "/Zc:trigraphs (三併詞替代) | Microsoft Docs"
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
  - "/Zc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zc 編譯器選項 (C++)"
  - "Conformance 編譯器選項"
  - "Zc 編譯器選項 (C++)"
  - "-Zc 編譯器選項 (C++)"
ms.assetid: e3d6058f-400d-4966-a3aa-800cfdf69cbf
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Zc:trigraphs (三併詞替代)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定 **\/Zc:trigraphs** 時，編譯器會使用對應的標點符號字元取代三併詞字元序列。  若要關閉三併詞替代，請指定 **\/Zc:trigraphs\-**。  根據預設值，**\/Zc:trigraphs** 為 off。  
  
## 語法  
  
```  
/Zc:trigraphs[-]  
```  
  
## 備註  
 三併詞由兩個連續問號 \("??"\) 後接唯一的第三個字元所組成。  例如，編譯器會使用 '\#' 字元取代 "??\=" 三併詞。  如果 C 原始程式檔所用的字元集不含某些標點符號字元的方便圖形表示，可改為使用三併詞。  
  
 如 C\/C\+\+ 三併詞的清單，以及示範如何使用三併詞的範例，請參閱[三併詞](../../c-language/trigraphs.md)。  
  
## 請參閱  
 [\/Zc \(一致性\)](../../build/reference/zc-conformance.md)   
 [三併詞](../../c-language/trigraphs.md)