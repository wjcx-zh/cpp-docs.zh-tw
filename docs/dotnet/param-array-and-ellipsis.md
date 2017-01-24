---
title: "Param 陣列和省略 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "函式多載化, 引數對應"
ms.assetid: 492e3f6c-1c4c-4e0c-a358-72f2d39c30be
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Param 陣列和省略
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從 Managed Extensions for C\+\+ 升級為 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 之後，解析多載函式呼叫 \(Function Call\) 的 param 陣列之優先順序已變更。  
  
 在 Managed Extensions 和新語法中，並未提供明確支援給 C\# 和 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 所支援的 param 陣列。  相反地，其中之一會以屬性 \(Attribute\) 標記一般陣列，如下所示：  
  
```  
void Trace1( String* format, [ParamArray]Object* args[] );  
void Trace2( String* format, Object* args[] );  
```  
  
 雖然這兩個陣列看起來一樣，但是 `ParamArray` 屬性會針對 C\# 或其他 CLR 語言的陣列加上標記，使其在每個引動過程都具備不同數量的項目。  Managed Extensions 和新語法之間的程式行為的變更，是在於多載函式集 \(Function Set\) 的解析，其中一個執行個體會宣告省略，而第二個執行個體會宣告 `ParamArray` 屬性，如下列由 Artur Laksberg 所提供的範例所示。  
  
```  
int fx(...); // 1  
int fx( [ParamArray] Int32[] ); // 2  
```  
  
 在 Managed Extensions 中，省略優先於屬性，這很合理，因為屬性不屬於語言的正式部分。  但是在新語法中，語言內就已經直接支援了 param 陣列，而且由於其具有較強型別 \(Strongly Typed\)，因此優先於省略。  因此在 Managed Extensions 中，呼叫  
  
```  
fx( 1, 2 );  
```  
  
 會解析為 `fx(…)`，而在新語法中則解析為 `ParamArray` 執行個體。  極少情況是程式行為和省略執行個體引動過程的相依性，比和 `ParamArray` 引動過程的相依性還大，這時將需要修改簽章 \(Signature\) 或呼叫。  
  
## 請參閱  
 [一般的語言變更](../dotnet/general-language-changes-cpp-cli.md)