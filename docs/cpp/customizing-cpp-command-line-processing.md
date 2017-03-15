---
title: "自訂 C++ 命令列處理 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_setenvp"
  - "_setargv"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_setargv 函式"
  - "_setenvp 函式"
  - "命令列, 處理"
  - "命令列, 處理引數"
  - "命令列處理"
  - "環境, 環境處理常式"
  - "啟始程式碼, 自訂命令列處理"
  - "隱藏環境處理"
ms.assetid: aae01cbb-892b-48b8-8e1f-34f22421f263
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 自訂 C++ 命令列處理
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定的  
 如果您的程式不接受命令列引數，您可以隱藏執行命令列處理的程式庫常式用法，藉此稍微節省空間。  這個常式稱為 **\_setargv**，將在[萬用字元展開](../cpp/wildcard-expansion.md)中加以說明。  若要隱藏其用法，請在包含 **main** 函式的檔案中定義不執行任何動作的常式，並將此常式命名為 **\_setargv**。  然後，您的 **\_setargv** 定義將會進行對 **\_setargv** 的呼叫，且不會載入程式庫版本。  
  
 同樣地，如果您從未透過 `envp` 引數存取過環境資料表，您可以自行提供空的常式，用以取代 **\_setenvp** 環境處理常式。  就像使用 **\_setargv** 函式一般，**\_setenvp** 必須宣告為 **extern "C"**。  
  
 您的程式可能會呼叫 C 執行階段程式庫中的 **spawn** 或 `exec` 系列常式。  如果是這種情況，您就不應該隱藏環境處理常式，因為這個常式會用來將環境從父處理序傳遞至子處理序。  
  
## END Microsoft 特定的  
  
## 請參閱  
 [main：程式啟動](../cpp/main-program-startup.md)