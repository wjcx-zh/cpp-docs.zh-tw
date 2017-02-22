---
title: "資源編譯器警告 RW4004 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RW4004"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RW4004"
ms.assetid: 596b6a89-9ce7-4ba7-bdcb-e8054c7efafa
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 資源編譯器警告 RW4004
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ASCII 字元與虛擬按鍵碼不同  
  
 VIRTKEY 類型快速鍵中的虛擬按鍵碼 \(Virtual Key Code\) 使用了字串常值 \(String Literal\)。  
  
 這項警告允許您繼續編譯，但請注意，如此所產生的快速鍵可能與您指定的字串不相符 \(VIRTKEY 使用的按鍵碼與 ASCII 快速鍵不同\)。  
  
 儘管字串常值在句法上有效，但您只能在使用 WINDOWS.h 中 **VK\_\*\#define** 值的情況下，才可確保獲得所需要的快速鍵。