---
title: "連結器工具警告 LNK4105 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4105"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4105"
ms.assetid: 6c7bebf4-4ea6-4533-a6ed-e563d43abbd7
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 連結器工具警告 LNK4105
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

選項 'option' 沒有指定引數；忽略選項  
  
 這個警告只發生在已設定 [\/LIBPATH](../../build/reference/libpath-additional-libpath.md) 選項時。  如果這個選項並未指定任何目錄，連結器便會忽略該選項並產生這個警告訊息。  
  
 如果您不需要覆寫現有的環境程式庫設定，請移除連結器命令列的 \/LIBPATH 選項。  如果您想要使用其他的程式庫搜尋路徑，請在 \/LIBPATH 選項後面指定其他路徑。  
  
## 範例  
  
```  
link /libpath:c:\filepath\lib bar.obj  
```  
  
 會引導連結器先到 `c:\filepath\lib`，再到預設位置搜尋必要的程式庫。