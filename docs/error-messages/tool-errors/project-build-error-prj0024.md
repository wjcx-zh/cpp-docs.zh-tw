---
title: "專案建置錯誤 PRJ0024 | Microsoft Docs"
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
  - "PRJ0024"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0024"
ms.assetid: 8bde6368-6c1b-4e04-bc5e-3c6d0b8fa1d7
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 專案建置錯誤 PRJ0024
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法將 Unicode 路徑 'path' 轉譯為使用者的 ANSI 字碼頁。  
  
 ***path***  是路徑字串的原始 Unicode 版本。  在有 Unicode 路徑無法直接轉譯為目前系統字碼頁 \(Code Page\) 的 ANSI 的情況下，就會發生這種錯誤。  
  
 如果您使用不是在您電腦上之字碼頁的系統所開發的專案，也可能發生這種錯誤。  
  
 針對這個錯誤的解決方法是，更新路徑來使用 ANSI 文字，或在您的電腦上安裝該字碼頁，並將它設為系統預設值。