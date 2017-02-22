---
title: "專案建置錯誤 PRJ0025 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "PRJ0025"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0025"
ms.assetid: 57725c78-bc63-44f3-9667-2969b2d7c41d
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 專案建置錯誤 PRJ0025
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

批次檔 'file' 包含無法轉譯成使用者 ANSI 字碼頁的 Unicode 內容。  
  
 ***UNICODE 檔案內容***  
  
 專案系統發現：自訂組建 \(Build\) 規則或建置事件中的 Unicode 內容無法適當地轉譯為使用者目前的 ANSI 字碼頁。  
  
 這個錯誤的解決方法是，更新建置規則或建置事件的內容來使用 ANSI，或在您的電腦上安裝該字碼頁，並將它設為系統預設值。  
  
 如需自訂建置步驟和建置事件的詳細資訊，請參閱[瞭解自訂建置步驟和建置事件](../../ide/understanding-custom-build-steps-and-build-events.md)。