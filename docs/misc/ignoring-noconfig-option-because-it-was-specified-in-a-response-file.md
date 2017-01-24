---
title: "因為在回應檔中已指定 /noconfig 選項，所以將會忽略該選項。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc2025"
  - "bc2025"
helpviewer_keywords: 
  - "BC2025"
ms.assetid: 87fb393d-e17f-4e50-8d98-d9dfeba30c3e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 因為在回應檔中已指定 /noconfig 選項，所以將會忽略該選項。
`/noconfig` 選項指示編譯器不要使用 Vbc.rsp 檔案進行編譯。 不過，編譯器會先處理 Vbc.rsp 檔案，再處理任何其他回應檔，因此編譯器無法接受回應檔中的 `/noconfig` 選項。  
  
 **錯誤 ID︰**BC2025  
  
### 更正這個錯誤  
  
1.  從回應檔中移除 `/noconfig` 選項。  
  
2.  叫用命令列編譯器時指定 `/noconfig` 選項。  
  
## 請參閱  
 [\/noconfig](../Topic/-noconfig.md)   
 [@ \(Specify Response File\)](../Topic/@%20\(Specify%20Response%20File\)%20\(Visual%20Basic\).md)