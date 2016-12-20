---
title: "__invlpg | Microsoft Docs"
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
  - "__invlpg"
  - "__invlpg_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "invlpg 指令"
  - "__invlpg 內建"
ms.assetid: 3fb3633f-d9b7-4ec0-9e7f-a7f2fa8ed794
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __invlpg
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 會產生 x86 `invlpg`指令，會轉譯對應緩衝區 \(TLB\) 會使得無效，網頁所指的記憶體與相關聯的`Address`。  
  
## 語法  
  
```  
void __invlpg(  
   void* Address  
);  
```  
  
#### 參數  
 \[in\] `Address`  
 64 位元位址。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__invlpg`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 內建`__invlpg`會發出一個秘密的指令，而是只適用於核心模式特殊權限層級 \(CPL\) 為 0。  
  
 只有使用與內建這個常式。  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)