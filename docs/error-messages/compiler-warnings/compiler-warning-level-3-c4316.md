---
title: "編譯器警告 (層級 3) C4316 | Microsoft Docs"
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
  - "C4316"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4316"
ms.assetid: 10371f01-aeb8-40ac-a290-59e63efa5ad4
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 3) C4316
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在堆積中配置的物件無法用於對齊此類型。  
  
 使用 `operator new` 配置的過度對齊物件可能沒有指定的對齊方式。  覆寫過度對齊 \(Over\-Aligned\) 類型的 [new 運算子](../../c-runtime-library/operator-new-crt.md)和 [delete 運算子](../../c-runtime-library/operator-delete-crt.md)，以便這些類型使用對齊的配置常式，例如 [\_aligned\_malloc](../../c-runtime-library/reference/aligned-malloc.md) 和 [\_aligned\_free](../../c-runtime-library/reference/aligned-free.md)。  下列範例會產生 C4316：  
  
```cpp  
// C4316.cpp  
// Test: cl /W3 /c C4316.cpp  
  
__declspec(align(32)) struct S {}; // C4324  
  
int main() {  
    new S; // C4316  
}  
```