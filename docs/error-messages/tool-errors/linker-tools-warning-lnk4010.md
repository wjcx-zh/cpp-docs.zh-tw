---
title: "連結器工具警告 LNK4010 | Microsoft Docs"
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
  - "LNK4010"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4010"
ms.assetid: 2824cf99-4174-4b60-a6e2-c01e9f1ee52d
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具警告 LNK4010
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無效的子系統版本號碼 number，假設使用預設的子系統版本  
  
 您可以指定影像的子系統版本 \([\/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md)\)。  每個子系統都有最小版本需求。  如果指定的版本低於最小版本，就會發生這項警告，而連結器就會直接使用預設子系統。