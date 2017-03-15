---
title: "隱含連結 | Microsoft Docs"
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
  - "隱含連結 [C++]"
  - "載入時間動態連結 [C++]"
  - "靜態載入連結 [C++]"
ms.assetid: 3ea4c316-4e70-4111-9944-c1b4ad00c605
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 隱含連結
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要隱含連結至 DLL，可執行檔必須先從 DLL 的提供者獲得下列資訊：  
  
-   包含匯出函式和 \(或\) C\+\+ 類別宣告的標頭檔 \(.h 檔\)。類別、函式和資料都必須具有 `__declspec(dllimport)`。如需詳細資訊，請參閱 [dllexport、dllimport](../cpp/dllexport-dllimport.md)。  
  
-   要連結的匯入程式庫 \([.lib 檔案](../build/reference/dot-lib-files-as-linker-input.md)\)\(當建置 DLL 時，連結器建立匯入程式庫\)。  
  
-   實質的 DLL \(.dll 檔案\)。  
  
 使用 DLL 的可執行檔必須包含的標頭檔，會在每個包含呼叫匯出函式原始程式檔 \(Source File\) 中包含匯出函式 \(或 C\+\+ 類別\)。  從程式設計的觀點來看，匯出函式的函式呼叫很類似其他任何的函式呼叫。  
  
 若要建置呼叫的可執行檔，您必須連結匯入程式庫。  如果您是使用外部的 Makefile，就要在您列出其他目的檔 \(.obj\) 或要連結程式庫的地方，指定匯入程式庫的檔案名稱。  
  
 作業系統必須要在載入呼叫的可執行檔時找到 DLL 檔案。  
  
## 您想要執行甚麼工作？  
  
-   [明確連結](../build/linking-explicitly.md)  
  
-   [判斷要使用哪一個連結方法](../build/determining-which-linking-method-to-use.md)  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [與匯入程式庫和匯出檔案一起使用](../build/reference/working-with-import-libraries-and-export-files.md)  
  
-   [Windows 用來找出 DLL 的搜尋路徑](../build/search-path-used-by-windows-to-locate-a-dll.md)  
  
## 請參閱  
 [將可執行檔連結至 DLL](../build/linking-an-executable-to-a-dll.md)