---
title: "編譯器命令列語法 | Microsoft Docs"
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
  - "cl.exe 編譯器, 命令列語法"
  - "語法, CL 編譯器命令列"
ms.assetid: acba2c1c-0803-4a3a-af25-63e849b930a2
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 編譯器命令列語法
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

CL 命令列使用下列語法：  
  
```  
CL [option...] file... [option | file]... [lib...] [@command-file] [/link link-opt...]  
```  
  
 下表說明 CL 命令的輸入。  
  
|Entry|意義|  
|-----------|--------|  
|*選項*|一個或多個 [CL 選項](../../build/reference/compiler-options.md)。  請注意，所有選項均適用於所有指定的原始程式檔。  選項是以正斜線 \(\/\) 或短橫線 \(–\) 所指定。  如果選項需要引數，選項的描述會記載選項與引數之間是否需要加一個空格。  選項名稱 \(除了 \/HELP 選項之外\) 要區分大小寫。  如需詳細資訊，請參閱 [CL 選項的順序](../../build/reference/order-of-cl-options.md)。|  
|`file`|一個或多個原始程式檔、.obj 檔或程式庫的名稱。  CL 會編譯原始程式檔並將 .obj 檔和程式庫的名稱傳遞給連結器 \(Linker\)。  如需詳細資訊，請參閱 [CL 檔名語法](../../build/reference/cl-filename-syntax.md)。|  
|*lib*|一個或多個程式庫名稱。  CL 會將這些名稱傳遞給連結器。|  
|*command\-file*|一個包含多個選項和檔名的檔案。  如需詳細資訊，請參閱 [CL 命令檔](../../build/reference/cl-command-files.md)。|  
|*link\-opt*|一個或多個[連結器選項](../../build/reference/linker-options.md)。  CL 會將這些選項傳遞給連結器。|  
  
 只要命令列上的字元數目不超過 1024 個 \(作業系統規定的限制\)，您可以指定任何數目的選項、檔名及程式庫名稱。  
  
 如需關於 cl.exe 傳回值的詳細資訊，請參閱 [cl.exe 的傳回值](../../build/reference/return-value-of-cl-exe.md)：  
  
> [!NOTE]
>  將來的 Windows 版本並不一定會維持命令列 1024 個字元的輸入限制。  
  
## 請參閱  
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [編譯器選項](../../build/reference/compiler-options.md)