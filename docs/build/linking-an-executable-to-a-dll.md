---
title: "將可執行檔連結至 DLL | Microsoft Docs"
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
  - "DLL [C++], 連結"
  - "動態載入連結 [C++]"
  - "可執行檔 [C++], 連結至 DLL"
  - "明確連結 [C++]"
  - "隱含連結 [C++]"
  - "連結 [C++], DLL"
  - "載入 DLL [C++]"
  - "執行階段 [C++], 連結"
ms.assetid: 7592e276-dd6e-4a74-90c8-e1ee35598ea3
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 將可執行檔連結至 DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可執行檔以下列兩種方式之一連結至 \(或載入\) DLL：  
  
-   [隱含連結](../build/linking-implicitly.md)  
  
-   [明確連結](../build/linking-explicitly.md)  
  
 隱含連結有時是當成靜態載入或載入時期動態連結。  明確連結有時是當成動態載入或執行階段動態連結。  
  
 有了隱含連結，使用 DLL 的可執行檔便可連結至 DLL 製作者提供的匯入程式庫 \(.lib 檔\)。  作業系統會在可執行檔要使用其載入的 DLL 時，載入 DLL。  用戶端可執行檔會像函式是包含在可執行檔內一般，呼叫 DLL 的匯出函式。  
  
 有了明確連結，使用 DLL 的可執行檔必須製作明確載入和卸載 DLL 的函式呼叫 \(Function Call\)，並且存取 DLL 的匯出函式。  用戶端可執行檔必須經由函式指標呼叫匯出函式。  
  
 可執行檔可以使用具任何一種連結方式的相同 DLL。  再者，這些機制之間並不會互相排斥，因此當一個可執行檔隱含地連結至 DLL 時，另一個可執行檔可以明確地連結至它。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [與匯入程式庫和匯出檔案一起使用](../build/reference/working-with-import-libraries-and-export-files.md)  
  
-   [決定要使用哪一個連結方法](../build/determining-which-linking-method-to-use.md)  
  
-   [Windows 用來找出 DLL 的搜尋路徑](../build/search-path-used-by-windows-to-locate-a-dll.md)  
  
## 請參閱  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)