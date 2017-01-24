---
title: "讀取範圍 | Microsoft Docs"
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
  - "C"
ms.assetid: 99de29ce-ab14-46f4-97e1-2081fd996b53
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 讀取範圍
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 4.9.6.2** 解譯虛線 \(–\) 字元，該字元不是 `fscanf` 函式中 % \[ 轉換之 scanlist 中的第一個字元，也不是最後一個字元  
  
 下面這行  
  
```  
fscanf( fileptr, "%[A-Z]", strptr);  
```  
  
 會將範圍 A\-Z 中任何數目的字元讀取到 `strptr` 所指向的字串中。  
  
## 請參閱  
 [程式庫函式](../c-language/library-functions.md)