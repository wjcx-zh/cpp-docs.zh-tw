---
title: "字串化運算子 (#) | Microsoft Docs"
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
  - "#"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "# 前置處理器運算子"
  - "引數 [C++], 轉換為字串"
  - "巨集 [C++], 將參數轉換為字串"
  - "前置處理器"
  - "前置處理器, 運算子"
  - "字串常值, 將巨集參數轉換為"
  - "字串化運算子"
ms.assetid: 1175dd19-4538-43b3-ad97-a008ab80e7b1
caps.latest.revision: 16
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 字串化運算子 (#)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

數字符號或「字串化」的運算子 \(**\#**\) 可將巨集參數轉換為字串常值，而不會擴充參數定義。  只會搭配接受引數的巨集使用。  如果出現在巨集定義的型式參數之前，巨集引動過程傳入的實質引數會以引號括住並且將視為字串常值。  然後字串常值會取代巨集定義中每個字串化運算子和型式參數的組合。  
  
> [!NOTE]
>  ANSI C 標準的 Microsoft C \(6.0 版和之前版本\) 擴充功能之前會展開字串常值和字元常數中的巨集型式引數，但目前已不再支援此功能。  使用字串化 \(**\#**\) 運算子可重寫依賴此擴充功能的程式碼。  
  
 實際引數的第一個語彙基元之前和最後一個語彙基元之後的空白字元則會予以忽略。  在實際引數中語彙基元之間的任何空白字元，在產生的字串常值中皆會縮短為單一空白字元。  因此，如果在實際引數的兩個語彙基元之間出現註解，將會縮短為單一空白字元。  產生的字串常值會自動與任何僅以空白字元分隔的相鄰字串常值串連。  
  
 此外，如果在字串常值中使用引數包含通常需要逸出序列時 \(例如引號 \(**"**\) 或反斜線 \(**\\**\) 字元\)，必要的逸出反斜線字元就會自動插入至該字元之前。  
  
 Visual C\+\+ 字串化運算子可能無法如預期的在所有情況下作用，請參閱 [16.3.2 \# 運算子](../misc/16-3-2-the-hash-operator.md)以取得詳細資訊。  
  
## 範例  
 下列範例中展示一項巨集定義，其中包含字串化運算子和叫用巨集的主函式：  
  
 這類引動過程會在前置處理期間展開並且產生下列程式碼：  
  
```  
int main() {  
   printf_s( "In quotes in the printf function call\n" "\n" );  
   printf_s( "\"In quotes when printed to the screen\"\n" "\n" );  
   printf_s( "\"This: \\\" prints an escaped double quote\"" "\n" );  
}  
```  
  
```  
// stringizer.cpp  
#include <stdio.h>  
#define stringer( x ) printf_s( #x "\n" )  
int main() {  
   stringer( In quotes in the printf function call );   
   stringer( "In quotes when printed to the screen" );     
   stringer( "This: \"  prints an escaped double quote" );  
}  
```  
  
  **In quotes in the printf function call**  
**"In quotes when printed to the screen"**  
**"This: \\"  prints an escaped double quote"**   
## 範例  
 下列範例示範如何展開巨集參數：  
  
```  
// stringizer_2.cpp  
// compile with: /E  
#define F abc  
#define B def  
#define FB(arg) #arg  
#define FB1(arg) FB(arg)  
FB(F B)  
FB1(F B)  
```  
  
## 請參閱  
 [前置處理器運算子](../preprocessor/preprocessor-operators.md)