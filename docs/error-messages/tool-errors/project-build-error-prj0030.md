---
title: "專案建置錯誤 PRJ0030 | Microsoft Docs"
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
  - "PRJ0030"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0030"
ms.assetid: c48b3727-e166-46e7-bcd7-3e5b2ac5c1d4
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 專案建置錯誤 PRJ0030
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

巨集展開發生錯誤，$\(macro\) 的評估遞迴超過 32 層。  
  
 此錯誤是由您巨集中的遞迴所造成。  例如，如果您將 **Intermediate Directory** 屬性 \(請參閱[一般屬性頁 \(專案\)](../../ide/general-property-page-project.md)\) 設定為 $\(IntDir\)，將會發生遞迴。  
  
 若要解決此錯誤，請不要以它們用來定義的巨集來定義巨集或屬性。