---
title: "#line 指示詞 (C/C++) | Microsoft Docs"
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
  - "#line"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "#line 指示詞"
  - "line 指示詞 (#line)"
  - "前置處理器, 指示詞"
ms.assetid: 585c1dc4-5184-4f01-98f4-80c1909744d7
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# #line 指示詞 (C/C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`#line` 指示詞呼叫前置處理器變更編譯器的內部儲存行號和檔名至特定行號和檔案名稱。  
  
## 語法  
  
```  
  
#line   
digit-sequence ["filename"]  
```  
  
## 備註  
 編譯器會使用這個行號和選擇性檔名來指向它在編譯期間發現的錯誤。  行號通常是指目前的輸入行，檔案名稱則指目前的輸入檔。  每次一行程式碼處理後，行號將會遞增。  
  
 *數字序列（digit\-sequence）* 值可以是任何整數常數。  在前置處理語彙基元時可以執行巨集取代，不過結果必須評估為正確的語法。  此 *檔名（filename）* 可以是任何字元組合，但必須以雙引號（**" "**）括住。  如果省略 *檔名* ，則前一個檔名維持不變。  
  
 您可以撰寫 `#line` 指示詞修改來源行號和檔案名稱。  轉譯器使用行號和檔名判斷預先定義巨集 **\_\_FILE\_\_** 和 **\_\_LINE\_\_**的值。  您可以在程式中使用這些巨集插入自述性的錯誤訊息。  如需這些預先定義巨集的詳細資訊，請參閱 [預先定義巨集](../preprocessor/predefined-macros.md)。  
  
 **\_\_FILE\_\_** 巨集展開為一個內容是檔名的字串，由雙引號 \(**" "**\)包住。  
  
 如果您變更行號和檔名，編譯器會忽略先前的值並以新的值繼續處理。  程式產生器通常用於 `#line` 指示詞，以產生錯誤訊息，指向至參考原來的程式檔，而非產生的程式檔。  
  
 以下範例說明 `#line` 和 **\_\_LINE\_\_** 和 **\_\_FILE\_\_** 巨集。  
  
 在這個陳述式，內部儲存的行號被設為 151，而檔案名稱變更為 `copy.c`。  
  
```  
#line 151 "copy.c"  
```  
  
 在此範例中，如果指定的「assertion」不是 true，巨集 `ASSERT` 使用預先定義巨集 **\_\_LINE\_\_** 和 **\_\_FILE\_\_** 印出有關原始程式檔的錯誤訊息。  
  
```  
#define ASSERT(cond)  
  
if( !(cond) )\  
{printf( "assertion error line %d, file(%s)\n", \  
__LINE__, __FILE__ );}  
```  
  
## 請參閱  
 [前置處理器指示詞](../preprocessor/preprocessor-directives.md)