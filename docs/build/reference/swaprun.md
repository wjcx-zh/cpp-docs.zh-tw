---
title: "/SWAPRUN | Microsoft Docs"
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
  - "/swaprun"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/SWAPRUN editbin 選項"
  - "SWAPRUN editbin 選項"
  - "-SWAPRUN editbin 選項"
ms.assetid: 6eefd7f3-ca47-48e3-8509-323d27cf4ae7
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /SWAPRUN
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/SWAPRUN:{[!]NET|[!]CD}  
```  
  
## 備註  
 這個選項可編輯影像檔，告知作業系統將影像檔複製到交換檔 \(Swap File\)，並從該處加以執行。  請對存放在網路或抽取式媒體上的影像檔使用這個選項。  
  
 您可加入或移除 NET 或 CD 限定詞 \(Qualifier\)：  
  
-   NET 指示影像檔存放在網路上。  
  
-   CD 指示影像檔存放在 CD\-ROM 或類似的抽取式媒體上。  
  
-   請使用 \!NET 和 \!CD 來達到與 NET 和 CD 相反的效果。  
  
## 請參閱  
 [EDITBIN 選項](../../build/reference/editbin-options.md)