---
title: "連結器工具警告 LNK4086 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4086"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4086"
ms.assetid: ea1eecbb-ba2c-41bb-9a4f-fa0808a4b92d
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 連結器工具警告 LNK4086
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

進入點 'function' 不是使用 'number' 位元組引數的 \_\_stdcall；映像可能無法執行  
  
 DLL 的進入點必須是 `__stdcall`。  請使用 [\/Gz](../../build/reference/gd-gr-gv-gz-calling-convention.md) 選項重新編譯這個函式，或於定義函式時指定 `__stdcall` 或 WINAPI。