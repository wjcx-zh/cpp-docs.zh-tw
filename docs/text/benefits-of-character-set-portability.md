---
title: "字元集移植性的優點 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "字元集 [C++], 好處"
  - "可移植性 [C++], 字元集"
ms.assetid: bd60b925-1498-4e4f-897b-4c8ce66edcf7
caps.latest.revision: 8
caps.handback.revision: 8
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# 字元集移植性的優點
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

即使現在不想國際化應用程式，使用 MFC 和 C 執行階段可攜性功能仍可得到下列好處：  
  
-   可移植的程式碼讓您的程式碼基底有彈性。  稍後您可以輕易的將之移向 Unicode 或 MBCS。  
  
-   使用 Unicode 可使得 Windows 2000 的應用程式更有效率。  因為 Windows 2000 使用 Unicode，所以必須轉譯傳入和傳出作業系統的非 Unicode 字串，這會造成過度耗用。  
  
-   使用 MBCS 可以讓 Windows 2000 之外的 Win32 平台 \(例如 Windows 95 或 Windows 98\) 具備國際化市場的支援能力。  
  
## 請參閱  
 [Unicode 和 MBCS](../text/unicode-and-mbcs.md)   
 [Unicode 的支援](../text/support-for-unicode.md)