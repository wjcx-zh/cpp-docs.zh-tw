---
title: "初始設定式清單 | Microsoft Docs"
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
  - "初始設定式清單"
ms.assetid: b3e53442-9809-4105-9226-ae845bd20cae
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# 初始設定式清單
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建構函式的初始設定式清單現在會在基底類別建構函式之前呼叫。  
  
## 備註  
 在 Visual C\+\+ 2005 之前，使用 Managed Extensions for C\+\+ 編譯時，會先呼叫基底類別建構函式，再呼叫初始設定式清單。  現在，在使用 **\/clr** 編譯時，會先呼叫初始設定式清單。  
  
## 請參閱  
 [一般的語言變更](../dotnet/general-language-changes-cpp-cli.md)