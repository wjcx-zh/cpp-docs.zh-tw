---
title: "其他啟動考量 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "在 main 之前初始化"
  - "程式啟動 [C++]"
  - "啟始程式碼"
ms.assetid: 0e942aa6-8342-447c-b068-8980ed7622bd
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 其他啟動考量
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 C\+\+ 中，物件建構和解構可能需要執行使用者程式碼。  因此，請務必了解在進入 **main** 之前進行了哪些初始化，以及在 **main** 結束之後叫用了哪些解構函式。\(如需物件的建構和解構的詳細資訊，請參閱[建構函式](../cpp/constructors-cpp.md)和[解構函式](../cpp/destructors-cpp.md)\)。  
  
 下列初始化會在進入 **main** 之前發生：  
  
-   靜態資料預設會初始化為零。  沒有明確初始設定式的所有靜態資料在執行其他程式碼之前會設定為零，包括執行階段初始化。  靜態資料成員仍必須明確定義。  
  
-   初始化轉譯單位中的全域靜態物件。  這可能會在進入 **main** 之前發生，或是在物件的轉譯單位中第一次使用任何函式或物件時發生。  
  
 **Microsoft 特定的**  
  
 在 Microsoft C\+\+ 中，全域靜態物件會在進入 **main** 之前進行初始化。  
  
 **END Microsoft 特定的**  
  
 彼此互相依存，但位於不同轉譯單位中的全域靜態物件可能會產生不正確的行為。  
  
## 請參閱  
 [啟動和終止](../cpp/startup-and-termination-cpp.md)