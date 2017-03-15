---
title: "連結器工具錯誤 LNK1107 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1107"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1107"
ms.assetid: a37a893d-5efa-4eba-8f40-6c5518b4b9d0
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 連結器工具錯誤 LNK1107
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

檔案無效或損毀：無法在 location 讀取  
  
 工具無法讀取該檔案。  請重新建立該檔案。  
  
 如果嘗試傳遞模組 \(.dll 或 .netmodule 副檔名建立 [\/clr: noAssembly](../../build/reference/clr-common-language-runtime-compilation.md) 或 [\/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)\) 給連結器;將 .obj 檔，LNK1107 也可能發生。  
  
 如果編譯下列範例：  
  
```  
// LNK1107.cpp  
// compile with: /clr /LD  
public ref class MyClass {  
public:  
   void Test(){}  
};  
```  
  
 然後在命令列上指定 **link LNK1107.dll**，就會接到 LNK1107 錯誤訊息。若要解決這項錯誤，請改為指定 **link LNK1107.obj**。