---
title: "@ (指定編譯器回應檔) | Microsoft Docs"
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
  - "@"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "@ 編譯器選項"
  - "cl.exe 編譯器, 指定回應檔"
  - "回應檔, C/C++ 編譯器"
ms.assetid: 400fffee-909d-4f60-bf76-45833e822685
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# @ (指定編譯器回應檔)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定編譯器回應檔。  
  
## 語法  
  
```  
@response_file  
```  
  
## Arguments  
 `response_file`  
 是含有編譯器命令的文字檔。  
  
## 備註  
 回應檔可以包含您能夠在命令列上指定的任何命令。  因此，如果您的命令列引數超過 127 個字元，這會很有用。  
  
 您無法從回應檔內部指定 **@** 選項。  換言之，回應檔不能再嵌入另一個回應檔。  
  
 您可以視需要從命令列指定任何數量的回應檔選項 \(例如 `@respfile.1 @respfile.2`\)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
-   您不能從開發環境內指定回應檔，必須要在命令列指定。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   這個編譯器選項無法以程式設計方式進行變更。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)