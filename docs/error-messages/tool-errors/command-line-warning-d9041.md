---
title: "命令列警告 D9041 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "D9041"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "D9041"
ms.assetid: ada8815f-4246-4e25-b57d-a7f16fa107cc
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# 命令列警告 D9041
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無效的值 'value' \(對 '\/option' 而言\)，假設為 'value'。指定這項警告時請在命令列加入 '\/analyze'  
  
 在 **\/wd**、**\/we**、**\/wo** 或 **\/wl** 命令列選項中加入程式碼分析警告編號，但未同時指定 **\/analyze** 命令列選項。  若要補救這個錯誤，請加入 **\/analyze** 命令列選項，或從適當的 **\/w** 命令列選項中移除無效的警告編號。  
  
## 範例  
 下列命令列範例會產生警告 D9041：  
  
```  
cl /EHsc /LD /wd6001 filename.cpp  
```  
  
 若要修正這個警告，請加入 **\/analyze** 命令列選項。  如果您的編譯器版本不支援 **\/analyze**，請從 **\/wd** 選項中移除無效的警告編號。  
  
## 請參閱  
 [命令列錯誤 D8000 至 D9999](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)   
 [編譯器選項](../../build/reference/compiler-options.md)