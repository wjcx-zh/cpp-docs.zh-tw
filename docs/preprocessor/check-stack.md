---
title: "check_stack | Microsoft Docs"
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
  - "vc-pragma.check_stack"
  - "check_stack_CPP"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "check_stack pragma"
  - "Pragma, check_stack"
  - "Pragma, check_stack 使用方式表格"
ms.assetid: f18e20cc-9abb-48b7-ad62-8d384875b996
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# check_stack
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果指定 **off** \(或 **–**\)，指示編譯器關閉堆疊探查，如果指定 **on** \(或 **\+**\)，則指示編譯器開啟堆疊探查。  
  
## 語法  
  
```  
  
      #pragma check_stack([ {on | off}] )  
#pragma check_stack{+ | –}  
```  
  
## 備註  
 如果未指定引數，根據預設值處理堆疊探查。  這個 pragma 會在顯示該 pragma 後在定義的第一個函式生效。  堆疊探查不是巨集，也不是產生內嵌的函式。  
  
 如果您不指定 **check\_stack** pragma 的引數，堆疊檢查會還原成在命令列指定的行為。  如需詳細資訊，請參閱[編譯器參考](../build/reference/compiler-options.md)。  下表摘要說明 **\#pragma check\_stack** 和 [\/Gs](../build/reference/gs-control-stack-checking-calls.md) 選項的互動。  
  
### 使用 check\_stack pragma  
  
|語法|使用<br /><br /> \/Gs 選項編譯？|動作|  
|--------|-----------------------|--------|  
|**\#pragma check\_stack\( \)** 或<br /><br /> **\#pragma check\_stack**|是|關閉後續函式的堆疊檢查|  
|**\#pragma check\_stack\( \)** 或<br /><br /> **\#pragma check\_stack**|否|開啟後續函式的堆疊檢查|  
|**\#pragma check\_stack\(on\)**<br /><br /> 或 **\#pragma check\_stack \+**|是或否|開啟後續函式的堆疊檢查|  
|**\#pragma check\_stack\(off\)**<br /><br /> 或 **\#pragma check\_stack –**|是或否|關閉後續函式的堆疊檢查|  
  
## 請參閱  
 [Pragma 指示詞和 \_\_Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)