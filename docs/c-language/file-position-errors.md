---
title: "檔案位置錯誤 | Microsoft Docs"
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
helpviewer_keywords: 
  - "檔案指標 [C++], 檔案位置錯誤"
ms.assetid: d5e59d8b-08c0-4927-a338-0b2d8234ce24
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 檔案位置錯誤
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 4.9.9.1, 4.9.9.4** 失敗時，`fgetpos` 或 `ftell` 函式要將巨集 `errno` 設定成的值  
  
 當 `fgetpos` 或 `ftell` 失敗時，如果位置無效，會將 `errno` 設定為資訊清單常數 `EINVAL`，如果檔案編號錯誤則會設為 EBADF。  這些常數都在 ERRNO.H 中定義。  
  
## 請參閱  
 [程式庫函式](../c-language/library-functions.md)