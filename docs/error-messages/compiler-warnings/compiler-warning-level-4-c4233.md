---
title: "編譯器警告 (層級 4) C4233 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4233"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4233"
ms.assetid: 9aa51fc6-8ef3-43b5-bafb-c9333cf60de3
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4233
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用非標準的擴充 : 僅在 C\+\+ 中支援 'keyword' 關鍵字，C 不支援  
  
 編譯器將您的來源程式碼編譯為 C 而不是 C\+\+，而且您使用了只在 C\+\+ 中有效的關鍵字。  如果來源程式檔的副檔名是 .c 或者您使用 [\/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)，編譯器會將您的來源程式檔編譯為 C。  
  
 此警告會自動提升為錯誤。  如果您要修改此行為，請使用 [\#pragma warning](../../preprocessor/warning.md)。  例如，若要在您的來源程式碼檔案，將 C4233 歸類為層級 4 的警告事件。  
  
```  
#pragma warning(2:4233)  
```  
  
 。