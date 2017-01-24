---
title: "編譯器警告 (層級 4) C4235 | Microsoft Docs"
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
  - "C4235"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4235"
ms.assetid: d4214799-d62c-4674-b4e2-9e201c303303
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4235
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用了非標準的擴充 : 這種架構不支援 'keyword' 關鍵字  
  
 編譯器不支援您使用的關鍵字。  
  
 此警告會自動提升為錯誤。  如果您要修改此行為，請使用 [\#pragma warning](../../preprocessor/warning.md)。  例如，若要將 C4235 變成層級 2 的警告，請使用下列程式碼行  
  
```  
#pragma warning(2:4235)  
```  
  
 。