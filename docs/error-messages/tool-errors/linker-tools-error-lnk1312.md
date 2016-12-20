---
title: "連結器工具錯誤 LNK1312 | Microsoft Docs"
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
  - "LNK1312"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1312"
ms.assetid: 48284abb-d849-43fc-ab53-45aded14fd8a
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具錯誤 LNK1312
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

檔案無效或損毀: 無法匯入組件  
  
 建置組件時，使用 **\/clr** 編譯的模組或組件以外之檔案是傳遞給 **\/ASSEMBLYMODULE** 連結器選項。如果您傳遞目的檔給 **\/ASSEMBLYMODULE**，就直接傳遞物件給連結器，而不傳遞給 **\/ASSEMBLYMODULE**。  
  
## 範例  
 下列範例建立了 .obj 檔。  
  
```  
// LNK1312.cpp  
// compile with: /clr /LD  
public ref class A {  
public:  
   int i;  
};  
```  
  
## 範例  
 下列範例將產生 LNK1312。  
  
```  
// LNK1312_b.cpp  
// compile with: /clr /LD /link /assemblymodule:LNK1312.obj  
// LNK1312 error expected  
public ref class M {};  
```