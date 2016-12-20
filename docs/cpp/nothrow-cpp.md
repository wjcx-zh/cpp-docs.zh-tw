---
title: "nothrow (C++) | Microsoft Docs"
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
  - "nothrow_cpp"
  - "nothrow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec 關鍵字 [C++], nothrow"
  - "nothrow __declspec 關鍵字"
ms.assetid: 0a475139-459c-4ec6-99e8-7ecd0d7f44a3
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# nothrow (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 可在函式的宣告中使用的 `__declspec` 擴充屬性。  
  
## 語法  
  
```  
  
return-type __declspec(nothrow) [call-convention] function-name ([argument-list])  
```  
  
## 備註  
 這個屬性會告知編譯器其所呼叫的已宣告函式絕對不會擲回例外狀況。  使用同步例外狀況處理模型時 \(現在為預設值\)，編譯器可以排除在這類函式中追蹤某些無法還原物件存留期的機制，並大幅降低程式碼大小。  指定下列前置處理器指示詞與下列三種函式宣告相同：  
  
```  
#define WINAPI __declspec(nothrow) __stdcall   
  
void WINAPI f1();  
void __declspec(nothrow) __stdcall f2();  
void __stdcall f3() throw();  
```  
  
 使用 `void __declspec(nothrow) __stdcall f2();` 的好處是您可以在一組函式上使用一個 API 定義 \(例如 `#define` 陳述式所示\)，以方便您指定 `nothrow`。  第三個宣告 `, void __stdcall f3() throw();` 是 C\+\+ 標準所定義的語法。  
  
 如需詳細資訊，請參閱[同步例外狀況處理](http://msdn.microsoft.com/zh-tw/81595fae-d8ab-4c14-9670-8d6639cc0369)。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_\_declspec](../cpp/declspec.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)