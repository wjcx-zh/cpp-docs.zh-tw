---
title: "__ptr32、__ptr64 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__ptr32_cpp"
  - "__ptr64_cpp"
  - "__ptr32"
  - "__ptr64"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__ptr32 關鍵字 [C++]"
  - "__ptr64 關鍵字 [C++]"
  - "_ptr32 關鍵字 [C++]"
  - "_ptr64 關鍵字 [C++]"
  - "ptr32 關鍵字 [C++]"
  - "ptr64 關鍵字 [C++]"
ms.assetid: afb563d8-7458-4fe7-9c30-bd4b5385a59f
caps.latest.revision: 9
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# __ptr32、__ptr64
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定的  
 `__ptr32` 代表 32 位元系統上的原生指標，而 `__ptr64` 代表 64 位元系統上的原生指標。  
  
 下列範例將示範如何宣告每一個這些類型的指標：  
  
```  
int * __ptr32 p32;  
int * __ptr64 p64;  
```  
  
 在 32 位元系統上，使用 `__ptr64` 宣告的指標會截斷為 32 位元指標。  在 64 位元系統上，使用 `__ptr32` 宣告的指標會強制轉型為 64 位元指標。  
  
> [!NOTE]
>  使用 `__ptr32` 進行編譯時，無法使用 `__ptr64` 或 **\/clr:pure**。  否則會產生 `Compiler Error C2472`。  
  
## 範例  
 下列範例將示範如何使用 `__ptr32` 和 `__ptr64` 關鍵字宣告和配置指標。  
  
```  
#include <cstdlib>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
  
    int * __ptr32 p32;  
    int * __ptr64 p64;  
  
    p32 = (int * __ptr32)malloc(4);  
    *p32 = 32;  
    cout << *p32 << endl;  
  
    p64 = (int * __ptr64)malloc(4);  
    *p64 = 64;  
    cout << *p64 << endl;  
}  
```  
  
  **32**  
**64**   
## END Microsoft 特定的  
  
## 請參閱  
 [基本類型](../cpp/fundamental-types-cpp.md)