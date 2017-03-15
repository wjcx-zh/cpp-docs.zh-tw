---
title: "SBCS 和 MBCS 資料類型 | Microsoft Docs"
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
  - "MBCS"
  - "SBCS"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "SBCS 和 MBCS 資料類型"
  - "資料類型 [C], MBCS 和 SBCS"
ms.assetid: 4c3ef9da-e397-48d4-800e-49dba36db171
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# SBCS 和 MBCS 資料類型
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

只處理多位元組字元的所有 Microsoft `MBCS` 執行階段程式庫常式或多位元組字元的位元組需要 `unsigned` `int` 引數 \(0x00 \<\= 字元值 \<\= 0xFFFF 和 0x00 \<\= 位元組值 \<等於 0xFF\)。  在字串內容處理多位元組字元的 `MBCS` 常式預期多位元組字元字串表示為 `unsigned` 的 `char` 指標。  
  
> [!CAUTION]
>  多位元組字元的每個位元組可以用 8 位元 `char`來表示。  然而，值大於 0x7F 且型別為`char`的`SBCS` 或 `MBCS`單一位元組字元為負值。  當這類字元直接被轉換成`int` 或 `long`時，結果 會由編譯器產生符號延伸而可能產生不可預期的結果。  
  
 因此表示多位元組字元的位元組當做 8 位元 `unsigned char`是最佳的。  或者，只要在將`char`型別的單一位元字元轉換成`int`或是`long` 之前將其轉換成`unsigned char`就能避免造成負面結果。  
  
 因為有些`SBCS` 字串處理函式\(帶有正負號\)接受`char*` 參數，所以在`_MBCS` 時會產生類型不符編譯器警告。  有三種方法可以避免這個警告，如下依效率列出的順序:  
  
1.  在 TCHAR.H 中使用型別安全內嵌函式。  這是預設行為。  
  
2.  藉著在命令列上定義 `_MB_MAP_DIRECT` 來使用 TCHAR.H 中的直接巨集。  如果您這樣做，您必須手動對應型別。  這是最快的方法，但並非型別安全。  
  
3.  在 TCHAR.H 中使用型別安全靜態連結程式庫函式。  若要這麼做，請在命令列上定義 `_NO_INLINING` 常數。  這是最慢但型別最安全的方法。  
  
## 請參閱  
 [國際化](../c-runtime-library/internationalization.md)   
 [依分類區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)