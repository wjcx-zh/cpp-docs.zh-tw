---
title: "編譯器錯誤 C3173 | Microsoft Docs"
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
  - "C3173"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3173"
ms.assetid: edf79e10-e8cf-4f76-8d33-ab9d05e974e9
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3173
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在 idl 合併中版本不相符  
  
 當目的檔 \(Object File\) 包含用前一版編譯器產生的內嵌 idl 時，會出現此錯誤。  編譯器會編入版本編號，以確保用來產生 idl 內容 \(內嵌於 .obj 檔\) 的編譯器與用來合併內嵌 idl 的是同一個編譯器。  
  
 請更新您的 Visual C\+\+ 安裝，以確保使用最新版本的工具。