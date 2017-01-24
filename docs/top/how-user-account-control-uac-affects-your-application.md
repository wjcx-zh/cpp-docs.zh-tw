---
title: "使用者帳戶控制 (UAC) 如何影響應用程式 | Microsoft Docs"
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
  - "UAC [C++]"
  - "安全性 [C++], 使用者帳戶控制"
  - "使用者帳戶 [C++]"
  - "使用者帳戶控制 [C++]"
ms.assetid: 0d001870-253e-4989-b689-f78035953799
caps.latest.revision: 5
caps.handback.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# 使用者帳戶控制 (UAC) 如何影響應用程式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用者帳戶控制 \(UAC\) 是 Windows Vista 的功能，可以讓使用者帳戶擁有有限的權限。  您可以在以下網站找到有關 UAC 的詳細資訊：  
  
-   [Windows Vista 使用者帳戶控制逐步指南](http://go.microsoft.com/fwlink/?linkid=53781)  
  
-   [開發人員於最少權限環境中開發應用程式的最佳實務作法與方針](http://go.microsoft.com/fwlink/?linkid=82444)  
  
-   [了解與設定 Windows Vista 中的使用者帳戶控制](http://go.microsoft.com/fwlink/?LinkId=82445)  
  
## 在啟用 UAC 後建置專案  
 如果您在停用 UAC 的情況下，在 Windows Vista 上建置 Visual C\+\+ 專案，而且在稍後啟用了 UAC，就必須清除及重新建置專案，才能夠使其正確運作。  
  
## 需要系統管理員權限的應用程式  
 根據預設，Visual C\+\+ 連結器 \(Linker\) 會以 `asInvoker` 的執行層級，將 UAC 片段內嵌到應用程式的資訊清單中。  如果您的應用程式需要系統管理員權限才能正確執行 \(例如，如果會修改登錄的 HKLM 節點，或是會寫入到磁碟上受保護的區域，如 Windows 目錄\)，您就必須修改應用程式。  
  
 第一個選項是修改資訊清單的 UAC 片段，將執行層級變更為 *requireAdministrator*。  然後，應用程式便會提示使用者，必須在執行前提供管理認證。  如需這項做法的詳細資訊，請參閱 [\/MANIFESTUAC \(將 UAC 資訊內嵌在資訊清單中\)](../build/reference/manifestuac-embeds-uac-information-in-manifest.md)。  
  
 第二個選項則是指定 **\/MANIFESTUAC:NO** 連結器選項，讓 UAC 片段不要內嵌到資訊清單中。  在此情況下，您的應用程式便會以虛擬化的方式執行。  您對登錄或檔案系統所做的任何變更，都不會在應用程式結束後持續。  
  
 下列流程圖描述應用程式將會如何根據是否有啟用 UAC，以及應用程式是否有 UAC 資訊清單來執行。  
  
 ![Windows Vista 載入器行為](../top/media/uacflowchart.png "UACflowchart")  
  
## 請參閱  
 [安全性最佳作法](../top/security-best-practices-for-cpp.md)