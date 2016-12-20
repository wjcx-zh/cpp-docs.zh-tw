---
title: "檔名部分語法 | Microsoft Docs"
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
  - "NMAKE 中的檔名部分語法"
  - "NMAKE 程式, 語法"
  - "語法, 檔名部分"
ms.assetid: 48fe38e0-3f3b-40e6-894c-330ee775a656
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 檔名部分語法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

命令中的檔名部分語法代表第一個相依檔名的元件 \(可能是隱含的相依性\)。  檔名元件是依指定而非存在於磁碟上的檔案磁碟、路徑、主檔名，和副檔名。  使用 **%s** 代表完整的檔名。  使用 **%&#124;**\[*parts*\]**F** \(跟隨在百分比符號之後的 &#124; 字元\) 以代表部分的檔名，在此處 *parts* 可以是下列字母其中的零或多個，順序不限。  
  
|字母|說明|  
|--------|--------|  
|無字母|完整名稱 \(與 **%s** 相同\)|  
|**d**|磁碟機|  
|**p**|路徑|  
|**f**|主檔名|  
|**e**|副檔名|  
  
 例如，如果檔名是 c:\\prog.exe：  
  
-   %s 將會是 c:\\prog.exe  
  
-   %&#124;F 將會是 c:\\prog.exe  
  
-   %&#124;dF 將會是 c  
  
-   %&#124;pF 將會是 c:\\  
  
-   %&#124;fF 將會是 prog  
  
-   %&#124;eF 將會是 exe  
  
## 請參閱  
 [Makefile 中的命令](../build/commands-in-a-makefile.md)