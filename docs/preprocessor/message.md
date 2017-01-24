---
title: "message | Microsoft Docs"
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
  - "message_CPP"
  - "vc-pragma.message"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "message pragma"
  - "Pragma, message"
ms.assetid: 67414f25-ed47-4079-a5dc-21d9d1a39754
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# message
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

傳送字串常值至標準輸出，而不終止編譯。  
  
## 語法  
  
```  
  
#pragma message( messagestring )  
```  
  
## 備註  
 **message** pragma 的常見用法是在編譯時期顯示告知性訊息。  
  
 *messagestring* 參數可以是展開為字串常值的巨集，而您可以串連此類巨集與任意組合的字串常值。  
  
 如果您在 **message** pragma 中使用預先定義的巨集，則該巨集應該傳回一個字串，否則您就必須將巨集的輸出轉換為字串。  
  
 下列程式碼片段使用 **message** pragma 在編譯期間顯示訊息：  
  
```  
// pragma_directives_message1.cpp  
// compile with: /LD  
#if _M_IX86 >= 500  
#pragma message("_M_IX86 >= 500")  
#endif  
  
#pragma message("")  
  
#pragma message( "Compiling " __FILE__ )   
#pragma message( "Last modified on " __TIMESTAMP__ )  
  
#pragma message("")  
  
// with line number  
#define STRING2(x) #x  
#define STRING(x) STRING2(x)  
  
#pragma message (__FILE__ "[" STRING(__LINE__) "]: test")  
  
#pragma message("")  
```  
  
## 請參閱  
 [Pragma 指示詞和 \_\_Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)