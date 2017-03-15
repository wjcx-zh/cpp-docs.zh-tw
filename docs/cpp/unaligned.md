---
title: "__unaligned | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__unaligned_cpp"
  - "__unaligned"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__unaligned 關鍵字 [C++]"
ms.assetid: 0cd83aad-1840-47e3-ad33-59bfcbe6375b
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# __unaligned
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您使用 `__unaligned` 修飾詞宣告指標時，編譯器會假設指標位址資料並未對齊。  因此，對於以 Itanium 處理器系列 \(Itanium Processor Family，IPF\) 電腦為目標的應用程式，編譯器會產生一次讀取一個未對齊之資料位元組的程式碼。  
  
## 備註  
 `__unaligned` 修飾詞可用於 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 和 [!INCLUDE[vcpritanium](../cpp/includes/vcpritanium_md.md)] 編譯器，但是只會影響到以 IPF 電腦目標的應用程式。  此修飾詞只描述定址資料的對齊，指標本身會假設為已對齊。  
  
 [!INCLUDE[vcpritanium](../cpp/includes/vcpritanium_md.md)] 處理器在存取未對齊的資料時會產生對齊錯誤，而處理錯誤的時間會使效能降低。  使用 `__unaligned` 修飾詞讓處理器一次讀取一個位元組的資料，並避免錯誤發生。  [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 應用程式不需要使用此修飾詞，因為 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 處理器會處理未對齊的資料，而不會產生錯誤。  
  
 如需對齊的詳細資訊，請參閱：  
  
-   [align](../cpp/align-cpp.md)  
  
-   [\_\_alignof 運算子](../cpp/alignof-operator.md)  
  
-   [pack](../preprocessor/pack.md)  
  
-   [\/Zp \(結構成員對齊\)](../build/reference/zp-struct-member-alignment.md)  
  
-   [結構對齊範例](../build/examples-of-structure-alignment.md)  
  
## 範例  
  
```  
// unaligned_keyword.cpp  
// compile with: /c  
// processor: x64 IPF  
#include <stdio.h>  
int main() {  
   char buf[100];  
  
   int __unaligned *p1 = (int*)(&buf[37]);  
   int *p2 = (int *)p1;  
  
   *p1 = 0;   // ok  
  
   __try {  
      *p2 = 0;  // throws an exception  
   }  
   __except(1) {  
      puts("exception");  
   }  
}  
```  
  
## 請參閱  
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)