---
title: "main：程式啟動 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc.main.startup"
  - "_tmain"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_tmain 函式"
  - "進入點, 程式"
  - "main 函式, 程式啟動"
  - "程式啟動 [C++]"
  - "啟始程式碼, main 函式"
  - "wmain 函式"
ms.assetid: f9581cd6-93f7-4bcd-99ec-d07c3c107dd4
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# main：程式啟動
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

名為 `main` 的特殊函式是執行所有 C 和 [!INCLUDE[TLA#tla_cpp](../cpp/includes/tlasharptla_cpp_md.md)] 程式的起點。  如果您要撰寫的程式碼遵守 [!INCLUDE[TLA#tla_unicode](../cpp/includes/tlasharptla_unicode_md.md)] 程式設計模型，您可以使用 `wmain` \(寬字元版本的 `main`\)。  
  
 編譯器不會預先定義 `main` 函式。  必須在程式文字中提供這個函式。  
  
 `main` 的宣告語法是  
  
```  
int main();  
```  
  
 或者可以選擇  
  
```  
int main(int argc, char *argv[], char *envp[]);  
```  
  
## Microsoft 特定的  
 `wmain` 的宣告語法如下：  
  
```  
int wmain( );  
```  
  
 或者可以選擇  
  
```  
int wmain(int argc, wchar_t *argv[], wchar_t *envp[]);  
```  
  
 您也可以使用在 TCHAR.h 中定義的 `_tmain`。  除非定義 \_UNICODE，否則 `_tmain` 會解析成 `main`。  在此情況下，`_tmain` 會解析成 `wmain`。  
  
 或者可以將 `main` 和 `wmain` 函式宣告為傳回 `void` \(無傳回值\)。  如果您將 `main` 或 `wmain` 宣告為傳回 `void`，就不能使用 [return](../cpp/return-statement-in-program-termination-cpp.md) 陳述式將結束代碼傳回至父處理序或作業系統。  若要在將 `main` 或 `wmain` 宣告為 `void` 時傳回結束代碼，您必須使用 [exit](../cpp/exit-function.md) 函式。  
  
## END Microsoft 特定的  
 `argc` 和 `argv` 的類型是由語言定義。  `argc`、`argv` 和 `envp` 都是傳統名稱，但編譯器不需使用。  如需詳細資訊和範例，請參閱 [引數定義](../cpp/argument-definitions.md)。  
  
## 請參閱  
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)   
 [使用 wmain 取代 main](../cpp/using-wmain-instead-of-main.md)   
 [main 函式限制](../cpp/main-function-restrictions.md)