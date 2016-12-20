---
title: "編譯器警告 (層級 1) C4772 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4772"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4772"
ms.assetid: dafe6fd8-9faf-41f5-9d66-a55838742c14
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4772
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#import 參考來自遺漏型別程式庫的型別; 'missing\_type' 當做替代符號使用  
  
 已使用 [\#import](../../preprocessor/hash-import-directive-cpp.md) 指示詞參考了型別程式庫。  然而，此型別程式庫包含對其他型別程式庫之參考，且不是以 `#import` 參考該型別程式庫。  編譯器找不到另一個 .tlb 檔案。  
  
 請注意，如果您使用 [\/I \(其他 Include 目錄\)](../../build/reference/i-additional-include-directories.md) 編譯器選項來指定這些目錄，編譯器將不會在不同的目錄中尋找型別程式庫。  如果您想要讓編譯器在不同的目錄中尋找型別程式庫，請將這些目錄加入至 PATH 環境變數。  
  
 根據預設，這項警告當成是個錯誤。  無法使用 \/W0 以隱藏 C4772。  
  
## 範例  
 這是重現 C4772 必須要有的第一個型別程式庫。  
  
```  
// c4772a.idl  
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12b")]  
library C4772aLib  
{  
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c100")]  
   enum E_C4772a  
   {  
      one, two, three  
   };  
};  
```  
  
## 範例  
 這是重現 C4772 必須要有的第二個型別程式庫。  
  
```  
// c4772b.idl  
// post-build command: del /f C4772a.tlb  
// C4772a.tlb is available when c4772b.tlb is built  
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12d")]  
library C4772bLib  
{  
   importlib ("c4772a.tlb");  
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12e")]  
   struct S_C4772b  
   {  
      enum E_C4772a e;  
   };  
};  
```  
  
## 範例  
 下列範例會產生 C4772：  
  
```  
// C4772.cpp  
// assumes that C4772a.tlb is not available to the compiler  
// #import "C4772a.tlb"  
#import "C4772b.tlb"   // C4772 uncomment previous line to resolve  
                       // and make sure c4772a.tlb is on disk  
```