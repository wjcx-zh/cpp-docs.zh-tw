---
title: "安全範本多載 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES"
  - "_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES"
  - "_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES"
  - "_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES"
  - "_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT"
  - "安全範本多載"
ms.assetid: 562741d0-39c0-485e-8529-73d740f29f8f
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 安全範本多載
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

許多 CRT 函式已被取代而建議使用較新，安全性增強版本 \(例如， `strcpy_s` 是 `strcpy`的更安全的取代\)。  CRT 提供範本多載幫助減輕較安全的變數轉換。  
  
 例如，因為 `strcpy` 已被取代，此程式碼會產生警告:  
  
 `char szBuf[10];`  
  
 `strcpy(szBuf, "test"); // warning: deprecated`  
  
 您可以忽略警告。  定義 `_CRT_SECURE_NO_WARNINGS`符號以隱藏警告或使用 `strcpy_s`以更新程式碼:  
  
 `char szBuf[10];`  
  
 `strcpy_s(szBuf, 10, "test"); // security-enhanced _s function`  
  
 範本多載提供其他選項。  定義 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` 為 1 啟用自動呼叫更安全的變數標準的 CRT 多載函式範本。  如果 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` 為 1，則對程式碼的變更不是必要的。  在幕後，對 `strcpy` 的呼叫會變更為呼叫 `strcpy_s` 的方式與自動提供的大小引數。  
  
 `#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1`  
  
 `...`  
  
 `char szBuf[10];`  
  
 `strcpy(szBuf, "test"); // ==> strcpy_s(szBuf, 10, "test")`  
  
 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` 不會影響使用計算的函式，例如 `strncpy`。  若要啟用計數函式樣板的多載，請將 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` 定義為 1。  不過，在進行設定之前，因此請確定您的程式碼會將字元計數，而非緩衝區的大小 \(此為一個常見錯誤\) 。  此外，如果呼叫安全變數，則在函式呼叫後明確地將 null 結束字元在緩衝區結尾的程式碼是不必要的。  如果您需要攔截行為，請參閱 [\_TRUNCATE](../c-runtime-library/truncate.md)。  
  
> [!NOTE]
>  巨集 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` 要求 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` 也會定義為 1。  如果 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` 已定義，在 1 和 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` 被定義為 0，應用程式不會執行任何範本多載。  
  
 定義 `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` 到 1 可加強 Variant \(結尾為「\_s 的」的範本\) 多載。  在這種情況下，否則，如果 `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` 為 1，則一小變更必須對原始程式碼:  
  
 `#define _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES 1`  
  
 `...`  
  
 `char szBuf[10];`  
  
 `strcpy_s(szBuf, "test"); // ==> strcpy_s(szBuf, 10, "test")`  
  
 需要變更函式的名稱 \(將「\_s」\);範本多載負責提供大小引數。  
  
 根據預設， `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` 和 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` 被定義為0 \(停用\) ，而且 `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` 是定義為 1 \(啟用\)。  
  
 請注意這些範本多載為靜態陣列才有作用。  動態配置的緩衝區需要額外的原始程式碼變更。  再次存取上述範例:  
  
 `#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1`  
  
 `...`  
  
 `char *szBuf = (char*)malloc(10);`  
  
 `strcpy(szBuf, "test"); // still deprecated; have to change to`  
  
 `// strcpy_s(szBuf, 10, "test");`  
  
 和這段程式碼：  
  
 `#define _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES 1`  
  
 `...`  
  
 `char *szBuf = (char*)malloc(10);`  
  
 `strcpy_s(szBuf, "test"); // doesn't compile; have to change to`  
  
 `// strcpy_s(szBuf, 10, "test");`  
  
## 請參閱  
 [CRT 中的安全性功能](../c-runtime-library/security-features-in-the-crt.md)   
 [CRT 程式庫功能](../c-runtime-library/crt-library-features.md)