---
title: "Windows 執行階段不支援的 CRT 函式 | Microsoft Docs"
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
  - "不支援的 CRT 函式, Windows 執行階段"
  - "Windows 執行階段, 不支援的 CRT 函式"
ms.assetid: bb8386d6-0ef8-460c-88d8-addff009b6f1
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# Windows 執行階段不支援的 CRT 函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

許多 C 執行階段 \(CRT\) 應用程式開發介面不能用於在 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 中執行的 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 應用程式。  這些應用程式會使用 \/ZW 編譯器旗標建置。  如需不支援的 CRT 函式清單，請參閱 [\/ZW 不支援的 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
 所有的 CRT 應用程式開發介面都會在本文件的[依字母順序排列的函式參考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)章節中描述。  
  
## 請參閱  
 [依分類區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)   
 [依字母順序排列的函式參考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)