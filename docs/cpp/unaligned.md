---
title: "__unaligned |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: __unaligned_cpp
dev_langs: C++
helpviewer_keywords: __unaligned keyword [C++]
ms.assetid: 0cd83aad-1840-47e3-ad33-59bfcbe6375b
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1c148803da11ea85857cb77753d2e6af6a6ae22e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="unaligned"></a>__unaligned
當您使用 `__unaligned` 修飾詞宣告指標時，編譯器會假設指標位址資料並未對齊。 因此，對於以 Itanium 處理器系列 (Itanium Processor Family，IPF) 電腦為目標的應用程式，編譯器會產生一次讀取一個未對齊之資料位元組的程式碼。  
  
## <a name="remarks"></a>備註  
 `__unaligned`修飾詞可用於[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]和[!INCLUDE[vcpritanium](../cpp/includes/vcpritanium_md.md)]編譯器，但是 IPF 電腦目標的影響只應用程式。 此修飾詞只描述定址資料的對齊，指標本身會假設為已對齊。  
  
 [!INCLUDE[vcpritanium](../cpp/includes/vcpritanium_md.md)]處理器它存取未對齊的資料，且處理錯誤的時間會使效能降低時，產生對齊錯誤。 使用 `__unaligned` 修飾詞讓處理器一次讀取一個位元組的資料，並避免錯誤發生。 此修飾詞不需要[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]應用程式因為[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]處理器處理未對齊的資料，而不發生錯誤。  
  
 如需對齊的詳細資訊，請參閱：  
  
-   [align](../cpp/align-cpp.md)  
  
-   [__alignof 運算子](../cpp/alignof-operator.md)  
  
-   [pack](../preprocessor/pack.md)  
  
-   [/Zp （結構成員對齊）](../build/reference/zp-struct-member-alignment.md)  
  
-   [結構對齊範例](../build/examples-of-structure-alignment.md)  
  
## <a name="example"></a>範例  
  
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
  
## <a name="see-also"></a>另請參閱  
 [關鍵字](../cpp/keywords-cpp.md)