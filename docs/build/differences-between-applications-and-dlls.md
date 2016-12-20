---
title: "應用程式和 DLL 之間的差異 | Microsoft Docs"
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
  - "應用程式 [C++], 和 DLL 比較"
  - "DLL [C++], 和應用程式的比較"
  - "可執行檔 [C++], DLL 和應用程式的比較"
ms.assetid: 8f271523-d8d0-4ad1-84d2-0c5645d7fd5b
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 應用程式和 DLL 之間的差異
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

雖然 DLL 和應用程式都是可執行程式模組，但是它們在許多方面卻是不同。  對使用者而言，最明顯的差異在於 DLL 不是可以直接執行的程式。  從系統觀點來看，應用程式和 DLL 之間有兩個基本差異：  
  
-   應用程式本身可以同時在系統中執行多個執行個體，而 DLL 只能有一個執行個體。  
  
-   應用程式可以擁有如堆疊、全域記憶體、檔案控制代碼 \(File Handle\) 和訊息佇列等，而 DLL 則不含這些。  
  
## 您想要執行甚麼工作？  
  
-   [從 DLL 匯出](../build/exporting-from-a-dll.md)  
  
-   [將可執行檔連結至 DLL](../build/linking-an-executable-to-a-dll.md)  
  
-   [初始化 DLL](../build/initializing-a-dll.md)  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [使用 DLL 的優點](../build/advantages-of-using-dlls.md)  
  
-   [非 MFC DLL：概觀](../build/non-mfc-dlls-overview.md)  
  
-   [靜態連結至 MFC 的標準 DLL](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [動態連結至 MFC 的標準 DLL](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [擴充 DLL：概觀](../build/extension-dlls-overview.md)  
  
## 請參閱  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)