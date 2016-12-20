---
title: "編譯器 COM 支援 | Microsoft Docs"
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
  - "cl.exe 編譯器, COM 支援"
  - "COM, 編譯器支援"
ms.assetid: 76a78442-f2a4-4985-9967-67e20773f847
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 編譯器 COM 支援
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定的  
 Visual C\+\+ 編譯器可直接讀取元件物件模型 \(COM\) 類型程式庫，以及內容轉譯成可在編譯時包含的 C\+\+ 原始程式碼。  語言擴充功能可協助您進行用戶端的 COM 程式設計。  
  
 使用 [\#import 前置處理器指示詞](../preprocessor/hash-import-directive-cpp.md)，編譯器可以讀取類型程式庫，並將其轉換成將 COM 介面描述為類別的 C \+\+ 標頭檔。  一組 `#import` 屬性可供使用者控制產生類別程式庫標頭檔的內容。  
  
 您可以使用 [\_\_declspec](../cpp/declspec.md) 擴充屬性 [uuid](../cpp/uuid-cpp.md) 將全域唯一識別項 \(GUID\) 指派給 COM 物件。  [\_\_uuidof](../cpp/uuidof-operator.md) 關鍵字可用來擷取與 COM 物件關聯的 GUID。  另一個 `__declspec` 屬性 [property](../cpp/property-cpp.md) 可用來針對 COM 物件的資料成員指定 **get** 和 **set** 方法。  
  
 提供一組支援全域函式和類別的 COM，以支援 **VARIANT** 和 `BSTR` 類型、實作智慧型指標，以及封裝由 `_com_raise_error`擲回的錯誤物件：  
  
-   [編譯器 COM 全域函式](../cpp/compiler-com-global-functions.md)  
  
-   [\_bstr\_t](../cpp/bstr-t-class.md)  
  
-   [\_com\_error](../cpp/com-error-class.md)  
  
-   [\_com\_ptr\_t](../cpp/com-ptr-t-class.md)  
  
-   [\_variant\_t](../cpp/variant-t-class.md)  
  
## END Microsoft 特定的  
  
## 請參閱  
 [編譯器 COM 支援類別](../cpp/compiler-com-support-classes.md)   
 [編譯器 COM 全域函式](../cpp/compiler-com-global-functions.md)