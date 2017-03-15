---
title: "連結器工具警告 LNK4237 | Microsoft Docs"
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
  - "LNK4237"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4237"
ms.assetid: 87bfec39-5241-464f-9feb-517b49f352ea
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具警告 LNK4237
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在從 'dll' 匯入時就已指定了 \/SUBSYSTEM:NATIVE；請使用 \/SUBSYSTEM:CONSOLE 或 \/SUBSYSTEM:WINDOWS。  
  
 在建置可直接使用下列一或多個 DLL 的 Windows \(Win32\) 應用程式時，會指定 [\/SUBSYSTEM:NATIVE](../../build/reference/subsystem-specify-subsystem.md)：  
  
-   kernel32.dll  
  
-   gdi32.dll  
  
-   user32.dll  
  
-   一種 msvcrt\* DLL。  
  
 透過不指定 **\/SUBSYSTEM:NATIVE**，就可解除這項警告。