---
title: "/CLRHEADER | Microsoft Docs"
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
  - "/CLRHEADER"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/CLRHEADER dumpbin 選項"
  - "CLRHEADER dumpbin 選項"
  - "-CLRHEADER dumpbin 選項"
ms.assetid: cf73424f-4541-47e2-b94e-69b95266ef2a
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /CLRHEADER
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/CLRHEADER file  
```  
  
## 備註  
 其中：  
  
 `file`  
 以 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) 所建置的映像檔。  
  
## 備註  
 CLRHEADER 顯示關於在任何 Managed 程式中使用的 .NET 標頭之資訊。  其輸出顯示 .NET 標頭的位置和大小 \(以位元組為單位\)，以及標頭中的區段。  
  
 只有 [\/HEADERS](../../build/reference/headers.md) DUMPBIN 選項可用在以 [\/GL](../../build/reference/gl-whole-program-optimization.md) 編譯器選項所產生的檔案上。  
  
 在以 \/clr 編譯的檔案上使用 \/CLRHEADER 時，在 dumpbin 輸出中將會有 **clr Header:** 區段。**flags** 的值會指出所使用的 \/clr 選項：  
  
-   0  \-\- \/clr \(映像可能會包含機器碼\)。  
  
-   1 \-\- \/clr:safe \(映像僅為 MSIL，能夠在任何 CLR 平台上執行，而且可能是可驗證的\)。  
  
-   3 \-\- \/clr:pure \(映像僅為 MSIL，但只能在 x86 平台上執行\)。  
  
 您也可以透過程式設計檢查是否已為 Common Language Runtime 建置了映像。如需詳細資訊，請參閱[如何：判斷影像是否為原生或 CLR](../../dotnet/how-to-determine-if-an-image-is-native-or-clr.md)。  
  
## 請參閱  
 [DUMPBIN 選項](../../build/reference/dumpbin-options.md)