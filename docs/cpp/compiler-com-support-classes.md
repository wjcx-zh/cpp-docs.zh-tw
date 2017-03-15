---
title: "編譯器 COM 支援類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_com_raise_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe 編譯器, COM 支援"
  - "COM, 編譯器支援"
ms.assetid: 6d800d9b-b902-4033-9639-740a30b06f88
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器 COM 支援類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 標準類別用來支援某些 COM 類型。  這些類別是在 comdef.h 中定義，而這些標頭檔是從類型程式庫產生的。  
  
|類別|用途|  
|--------|--------|  
|[\_bstr\_t](../cpp/bstr-t-class.md)|包裝 `BSTR` 類型可提供有用的運算子和方法。|  
|[\_com\_error](../cpp/com-error-class.md)|定義在大部分失敗的情況下，由 [\_com\_raise\_error](../cpp/com-raise-error.md) 所擲回的錯誤物件。|  
|[\_com\_ptr\_t](../cpp/com-ptr-t-class.md)|封裝 COM 介面指標，以及自動化 `AddRef`、**Release** 和 `QueryInterface` 所需的呼叫。|  
|[\_variant\_t](../cpp/variant-t-class.md)|包裝 **VARIANT** 類型可提供有用的運算子和方法。|  
  
## END Microsoft 特定的  
  
## 請參閱  
 [編譯器 COM 支援](../cpp/compiler-com-support.md)   
 [編譯器 COM 全域函式](../cpp/compiler-com-global-functions.md)   
 [C\+\+ 語言參考](../cpp/cpp-language-reference.md)