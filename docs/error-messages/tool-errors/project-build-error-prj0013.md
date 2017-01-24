---
title: "專案建置錯誤 PRJ0013 | Microsoft Docs"
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
  - "PRJ0013"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0013"
ms.assetid: 95e7bafd-63c8-4b2d-b778-f19cdf9ba36c
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 專案建置錯誤 PRJ0013
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

系統資源可能會非常低。無法建立啟動建置所需的管道。  
  
 此錯誤指出系統資源低下。  若要解決此錯誤，請降低其他處理程序\/應用程式使用的系統資源。  
  
 如果您的安全性等級不足以建立管道 \(請參閱 [CreatePipe](http://msdn.microsoft.com/library/windows/desktop/aa365152.aspx) \(英文\)\)，則也可能會發生此錯誤。