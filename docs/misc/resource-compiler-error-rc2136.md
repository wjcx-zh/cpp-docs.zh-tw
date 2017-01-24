---
title: "資源編譯器錯誤 RC2136 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "RC2136"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC2136"
ms.assetid: 4e9b2ff1-402c-4ec4-8610-fc8fd5f213c0
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# 資源編譯器錯誤 RC2136
在 EXSTYLE\=\<flags\> 中遺漏 '\='  
  
 **EXSTYLE** \(擴充樣式旗標\) 陳述式遺漏等號 \(**\=**\)。 當 **EXSTYLE** 內嵌在 **DIALOG** 或 **MENU** 陳述式時，必須具有下列格式：  
  
```  
EXSTYLE=FLAGS  
```