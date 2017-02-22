---
title: "編譯和連結多執行緒程式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "編譯多執行緒程式"
  - "編譯原始程式碼 [C++], 多執行緒程式"
  - "連結 [C++], 多執行緒程式"
  - "多執行緒 [C++], 編譯的程式"
  - "多執行緒 [C++], 連結程式"
  - "執行緒 [C++], 編譯的程式"
  - "執行緒 [C++], 連結程式"
ms.assetid: 27589afc-daf2-4f26-b868-a99de5c9dfec
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯和連結多執行緒程式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在[多執行緒 C 程式範例](../parallel/sample-multithread-c-program.md)中介紹了 Bounce.c 程式。  
  
 預設會以多執行緒方式編譯程式。  
  
#### 若要從發展環境中編譯和連結 Bounce.c 多執行緒程式  
  
1.  在 \[**檔案**\] 功能表上，按一下 \[**新增**\]，然後按一下 \[**專案**\]。  
  
2.  在 \[**專案類型**\] 窗格中，按一下 \[**Win32**\]。  
  
3.  在 \[**範本**\] 窗格中按一下 \[**Win32 主控台應用程式**\]，然後為專案命名。  
  
4.  將包含 C 原始程式碼的檔案加入至專案。  
  
5.  在 \[**建置**\] 功能表上按一下 \[**建置**\] 命令來建置專案。  
  
#### 若要從命令列編譯和連結 Bounce.c 多執行緒程式  
  
1.  編譯及連結此程式：  
  
    ```  
    CL BOUNCE.C  
    ```  
  
## 請參閱  
 [使用 C 和 Win32 進行多執行緒處理](../parallel/multithreading-with-c-and-win32.md)