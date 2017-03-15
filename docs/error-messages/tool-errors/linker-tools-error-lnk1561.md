---
title: "連結器工具錯誤 LNK1561 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1561"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1561"
ms.assetid: cb0b709b-7c9c-4496-8a4e-9e1e4aefe447
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 連結器工具錯誤 LNK1561
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

必須定義進入點  
  
 連結器找不到任何進入點 \(Entry Point\)。  您可能想要以連結 DLL 的方式來連結，此時您應該使用 [\/DLL](../../build/reference/dll-build-a-dll.md) 選項來連結。  您可能也忘了指定進入點的名稱；請以 [\/ENTRY](../../build/reference/entry-entry-point-symbol.md) 選項來連結。  
  
 否則，您就應該在程式碼中包含 main、wmain、WinMain 或 wMain 函式。  
  
 如果您使用 [LIB](../../build/reference/lib-reference.md)，並打算建置 .dll，則導致此錯誤的其中一個原因是您提供了 .def 檔。  若是如此，請從組建中移除 .def 檔。  
  
 下列範例會產生 LNK1561：  
  
```  
// LNK1561.cpp  
// LNK1561 expected  
int i;  
// add a main function to resolve this error  
```