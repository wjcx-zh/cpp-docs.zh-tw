---
title: "語彙基元 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- tokens [C++]
- parsing, C++ tokens
- translation units
- white space, in C++ tokens
ms.assetid: aa812fd0-6d47-4f3f-aee0-db002ee4d8b9
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 852165a345b36c2ea07d18334b050d5fcb8f7bc7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="tokens-c"></a>語彙基元 （c + +）
語彙基元是 C++ 程式中對編譯器有意義的最小項目。 C++ 剖析器可辨識下列語彙基元類型：識別項、關鍵字、常值、運算子、標點符號和任何其他分隔符號。 這些語彙基元資料流組成轉譯單位。  
  
 語彙基元通常由 *「空白字元」*(White Space) 分隔。 空白字元可以是下列一項或多項：  
  
-   空白  
  
-   水平或垂直定位字元  
  
-   新行  
  
-   換頁字元  
  
-   註解  
  
 剖析器可辨識關鍵字、識別項、常值、運算子和標點符號。 如需特定語彙基元類型的相關資訊，請參閱 [關鍵字](../cpp/keywords-cpp.md)、 [識別項](../cpp/identifiers-cpp.md)、 [數值、布林值和指標常值](../cpp/numeric-boolean-and-pointer-literals-cpp.md)、 [字串和字元常值](../cpp/string-and-character-literals-cpp.md)、 [使用者定義常值](../cpp/user-defined-literals-cpp.md)、 [C++ 內建運算子、優先順序和關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)，以及 [標點符號](../cpp/punctuators-cpp.md)。 除了分隔語彙基元所需的空白字元之外，其他空白字元都會予以忽略。  
  
 前置處理語彙基元會用於前置處理階段中，以產生傳遞至編譯器的語彙基元資料流。 前置處理語彙基元分類包括標頭名稱、識別項、前置處理數值、字元常值、字串常值、前置處理運算子和標點符號，以及不符合其他任何一個分類的單一非空白字元。 字元和字串常值可以是使用者定義常值。 前置處理語彙基元可以用空白字元或註解來分隔。  
  
 剖析器使用從左至右掃描的輸入字元來建立可能的最長語彙基元，藉此區隔語彙基元與輸入資料流。 請參考下列程式碼片段：  
  
```  
a = i+++j;  
```  
  
 撰寫程式碼的程式設計人員可能想要這兩個陳述式之一：  
  
```  
a = i + (++j)  
  
a = (i++) + j  
```  
  
 由於剖析器從輸入資料流建立可能的最長語彙基元，它選擇第二個解譯，產生語彙基元 `i++`、 `+`和 `j`。  
  
## <a name="see-also"></a>請參閱  
 [語彙慣例](../cpp/lexical-conventions.md)