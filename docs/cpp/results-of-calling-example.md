---
title: "呼叫範例的結果 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "範例 [C++], 呼叫的結果"
  - "結果, __cdecl 呼叫"
  - "結果, __fastcall 關鍵字呼叫"
  - "結果, __stdcall 呼叫"
  - "結果, thiscall 呼叫"
ms.assetid: aa70a7cb-ba1d-4aa6-bd0a-ba783da2e642
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 呼叫範例的結果
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定的  
  
## \_\_cdecl  
 C 裝飾函式名稱為 "\_MyFunc"。  
  
 ![CDECL 呼叫慣例](../cpp/media/vc37i01.png "vc37I01")  
\_\_cdecl 呼叫慣例  
  
## \_\_stdcall 和 thiscall  
 C 裝飾名稱 \(`__stdcall`\) 為 "\_MyFunc@20"。C\+\+ 裝飾名稱為機密。  
  
 ![&#95;&#95;stdcall 和 thiscall 呼叫慣例](../cpp/media/vc37i02.png "vc37I02")  
\_\_stdcall 和 thiscall 呼叫慣例  
  
## \_\_fastcall  
 C 裝飾名稱 \(`__fastcall`\) 為 "@MyFunc@20"。C\+\+ 裝飾名稱為機密。  
  
 ![&#95;&#95;fastcall 呼叫慣例](../cpp/media/vc37i03.png "vc37I03")  
\_\_fastcall 呼叫慣例  
  
### END Microsoft 特定的  
  
## 請參閱  
 [呼叫範例：函式原型和呼叫](../cpp/calling-example-function-prototype-and-call.md)