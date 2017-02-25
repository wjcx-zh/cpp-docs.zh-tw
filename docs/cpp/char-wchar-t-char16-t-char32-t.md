---
title: "char、wchar_t、char16_t、char32_t | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "char_cpp"
  - "char16_t_cpp"
  - "whchar_t_cpp"
  - "char32_t_cpp"
dev_langs: 
  - "C++"
ms.assetid: 6b33e9f5-455b-4e49-8f12-a150cbfe2e5b
caps.latest.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 2
---
# char、wchar_t、char16_t、char32_t
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

類型 char、wchar\_t、char16\_t 和 char32\_t 是內建類型，代表英數字元，以及非英數字符和非列印字元。  char 的大小是 8 個位元、wchar\_t 和 char16\_t 的大小是 16 個位元，而 char32\_t 是 32 個位元。  
  
## 語法  
  
```vb  
char     ch1{ 'a' };  
wchar_t  ch2{ 'a' }; // or {L'a'}  
char16_t ch3{ L'a' };// or {L'a'}  
char32_t ch4{ L'a' };// or {L'a'}  
```  
  
## 備註  
 `char` 類型是 C 和 C\+\+ 中的原始字元類型。  它可以用來儲存來自 ASCII 字元集、任何 ISO\-8859 字元集或 UTF\-8 字元集的字元。  類型 `unsigned char` 通常用來代表非 C\+\+ 中內建類型的*「位元組」*\(Byte\)。  char 類型不適用於許多語言的文字。  一般而言，現代程式應該使用其中一個寬字元類型來代表文字。  Unicode 是  
  
 在 C\+\+ 標準程式庫中，basic\_string 類型是專為窄和寬字串特製化。  字元的類型是 char 時，請使用 std::string，字元的類型是 wchar\_t 時，則請使用 std::wstring。  其他代表文字的類型 \(包括 std::stringstream 和 std::cout\) 具有窄和寬字串的特製化。  
  
## 需求