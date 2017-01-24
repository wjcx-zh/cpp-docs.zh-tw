---
title: "編譯器錯誤 C2530 | Microsoft Docs"
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
  - "C2530"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2530"
ms.assetid: b790a312-48df-4a6a-9e27-be2c5f32f16c
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2530
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 參考必須初始化  
  
 當宣告參考時，您必須將它初始化，除非它已經：  
  
-   使用 [extern](../../cpp/using-extern-to-specify-linkage.md) 關鍵字宣告。  
  
-   宣告為類別、結構或等位的一個成員 \(並且已在建構函式中初始化\)。  
  
-   宣告為函式宣告或定義中的一個參數。  
  
-   宣告為函式的傳回型別。  
  
 下列範例會產生 C2530：  
  
```  
// C2530.cpp  
int main() {  
   int i = 0;  
   int &j;   // C2530  
   int &k = i;   // OK  
}  
```