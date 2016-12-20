---
title: "CL 命令檔 | Microsoft Docs"
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
  - "cl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe 編譯器, 命令檔"
  - "命令檔"
  - "命令檔, CL 編譯器"
ms.assetid: ec3cea06-2af0-4fe9-a94c-119c9d31b3a9
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# CL 命令檔
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

命令檔是文字檔，含有您可以在[命令列](../../build/reference/compiler-command-line-syntax.md)上輸入或使用 [CL 環境變數](../../build/reference/cl-environment-variables.md)指定的選項及檔名。  CL 可以接受編譯器命令檔做為 CL 環境變數中或命令列上的引數。  與命令列或 CL 環境變數的差異在於，命令檔可以讓您使用多行的選項和檔名。  
  
 命令檔中的選項和檔名的處理方式取決於命令檔名稱在 CL 環境變數中或命令列上的位置。  但是，如果 \/link 選項出現在命令檔中，則在該行中其餘部分的所有選項都會被傳遞給連結器。  命令檔中後續各行裡的選項以及命令列上在命令檔引動過程之後的選項仍然會被當做編譯器選項接受。  如需有關選項順序如何影響其解譯的詳細資訊，請參閱 [CL 選項的順序](../../build/reference/order-of-cl-options.md)。  
  
 命令檔不可包含 CL 命令。  每個選項都必須在同一行開始和結束；您不可以使用反斜線 \(\\\) 來結合跨兩行的選項。  
  
 命令檔是由一個 @ 符號後接一個檔名來指定；檔名可以指定絕對路徑或相對路徑。  
  
 例如，假設下列命令是在名為 RESP 的檔案中：  
  
```  
/Og /link LIBC.LIB  
```  
  
 而且您指定了下列 CL 命令：  
  
```  
CL /Ob2 @RESP MYAPP.C  
```  
  
 則 CL 的整個命令會如下所示：  
  
```  
CL /Ob2 /Og MYAPP.C /link LIBC.LIB  
```  
  
 請注意，命令列和命令檔命令已實際上結合起來了。  
  
## 請參閱  
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [編譯器選項](../../build/reference/compiler-options.md)