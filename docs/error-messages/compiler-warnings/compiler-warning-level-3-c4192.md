---
title: "編譯器警告 (層級 3) C4192 | Microsoft Docs"
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
  - "C4192"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4192"
ms.assetid: ea5f91fa-8c96-4f3f-ac42-0c8a86d4e5df
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 3) C4192
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

自動排除 'name'，於匯入型別程式庫 'library' 時  
  
 `#import` 程式庫，包含了一個同時定義在 Win32 系統標頭的 *name* 項目。  由於型別程式庫的限制，如 **IUnknown** 或 GUID 之類的名稱經常是定義在型別程式庫中，從系統標頭複製定義。  `#import` 會偵測這些項目，並拒絕將它們包含在 .tlh 和 .tli 標頭檔中。  
  
 若要覆寫這種行為，請使用 `#import` 屬性 [no\_auto\_exclude](../../preprocessor/no-auto-exclude.md) 和 [include\(\)](../../preprocessor/include-parens.md)。