---
title: "區塊範圍的名稱連結 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "區塊範圍 [C++]"
  - "外部連結, 範圍連結規則"
  - "連結 [C++], 範圍連結規則"
  - "名稱 [C++], 範圍連結規則"
  - "範圍 [C++], 連結規則"
ms.assetid: 73efa91a-f761-47f7-bbd9-9f9e3508e218
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 區塊範圍的名稱連結
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列連結規則適用於具有區塊範圍的名稱 \(區域名稱\)：  
  
-   除非先前已宣告為 `extern`static，否則宣告為  **的名稱會具有外部連結。**  
  
-   具有區塊範圍的所有其他名稱都不具有連結。  
  
## 請參閱  
 [程式和連結](../cpp/program-and-linkage-cpp.md)