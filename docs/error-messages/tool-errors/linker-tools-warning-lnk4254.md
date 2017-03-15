---
title: "連結器工具警告 LNK4254 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4254"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4254"
ms.assetid: 6f41dfb3-ca21-40d3-bac7-b637e578efa4
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 連結器工具警告 LNK4254
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

區段 'section1' \(offset\) 以不同的屬性合併到 'section2 \(offset\)  
  
 一個區段的內容合併到另一個區段中，但這兩個區段的屬性不同。  您的程式很可能會提供未預期的結果。  例如，您要資料為唯讀，但現在可能是在可寫入區段中。  
  
 若要修正 LNK4254 錯誤，請修改或移除合併要求。  
  
 當您以 x86 機器和具有 Visual C\+\+ 的 Windows CE \(ARM、MIPS、SH4 和 Thumb\) 為目標時，CRT 區段會是唯讀的。  如果程式碼依賴之前的行為 \(.CRT 區段為讀取\/寫入\)，您可能會看到非預期的行為。  
  
 如需詳細資訊，請參閱：  
  
-   [\/MERGE \(結合區段\)](../../build/reference/merge-combine-sections.md)  
  
-   [註解](../../preprocessor/comment-c-cpp.md)  
  
## 範例  
 下列範例會產生 LNK4254。  
  
```  
// LNK4254.cpp  
// compile with: /W1 /link /WX  
// LNK4254 expected  
#pragma comment(linker, "/merge:.data=.text")  
int main() {}  
```