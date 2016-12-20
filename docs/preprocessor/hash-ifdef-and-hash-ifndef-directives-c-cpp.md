---
title: "#ifdef 和 #ifndef 指示詞 (C/C++) | Microsoft Docs"
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
  - "#ifndef"
  - "#ifdef"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "#ifdef 指示詞"
  - "#ifndef 指示詞"
  - "ifdef 指示詞 (#ifdef)"
  - "ifndef 指示詞 (#ifndef)"
  - "前置處理器, 指示詞"
ms.assetid: 2b0be69d-9e72-45d8-8e24-e4130fb2455b
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# #ifdef 和 #ifndef 指示詞 (C/C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**\#ifdef** 和 **\#ifndef** 指示詞執行的工作，與搭配 **defined**\(*identifier*\) 使用的 `#if` 指示詞執行的工作相同。  
  
## 語法  
  
```  
#ifdef identifier  
#ifndef identifier  
  
// equivalent to  
#if defined identifier  
#if !defined identifier  
```  
  
## 備註  
 您可以在任何可以使用 `#if` 的位置使用 **\#ifdef** 和 **\#ifndef** 指示詞。  **\#ifdef** *identifier* 陳述式在已定義 *identifier* 的情況下相當於  `#if 1` ，而在未定義 *identifier* 或使用 `#undef` 指示詞取消定義的情況下，則相當於  `#if 0` 。  這些指示詞只會檢查 `#define` 所定義的識別項是否存在，不適用於 C 或 C\+\+ 原始程式碼中宣告的識別項。  
  
 提供這些指示詞的目的只是為了保留與舊版語言的相容性。  建議您使用**defined\(** *identifier* **\)** 常數運算式搭配 `#if` 指示詞。  
  
 **\#ifndef** 指示詞會檢查與 **\#ifdef** 所檢查之條件相反的條件。  如果尚未定義識別項 \(或是已使用 `#undef` 移除其定義\)，則條件為 true \(非零\)。  否則，條件為 false \(0\)。  
  
 **Microsoft 特定的**  
  
 *identifier* 可以從命令列使用 \/D 選項傳遞。  使用 \/D 最多可以指定 30 個巨集。  
  
 這個選項在檢查定義是否存在時很實用，因為可以從命令列傳遞定義。  例如：  
  
```  
// ifdef_ifndef.CPP  
// compile with: /Dtest /c  
#ifndef test  
#define final  
#endif  
```  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [前置處理器指示詞](../preprocessor/preprocessor-directives.md)