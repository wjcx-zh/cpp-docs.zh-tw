---
title: "針對每個檔案使用的先行編譯標頭的一致性規則 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pch 檔案, 一致性原則"
  - "PCH 檔案, 一致性原則"
  - "先行編譯標頭檔, 一致性原則"
ms.assetid: afd49365-48bc-41f4-b700-fe8297b944a1
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 針對每個檔案使用的先行編譯標頭的一致性規則
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[\/Yu](../../build/reference/yu-use-precompiled-header-file.md) 編譯器選項可讓您指定要使用哪一個先行編譯標頭 \(PCH\) 檔。  
  
 在使用 PCH 時，除非您另行指定，否則編譯器會假設您是使用相同的編譯環境，也就是建立 PCH 時所使用的環境：使用一致的編譯器選項、Pragma 等等。  如果編譯器偵測到不一致，它會發出警告並識別可能的不一致之處。  這種警告並不一定指示 PCH 的問題；它們只是警告您可能的衝突。  下列章節說明 PCH 的一致性需求。  
  
## 編譯器選項一致性  
 在使用 PCH 時，下列編譯器選項會觸發 \(Trigger\) 不一致警告：  
  
-   在建立 PCH 的編譯和現行編譯之間，使用前置處理器 \(Preprocessor\) \(\/D\) 選項所建立的巨集必須相同。  並不會檢查已定義常數的狀態，但若是這些狀態改變，則可能發生無法預期的結果。  
  
-   PCH 不適用於 \/E 和 \/EP 選項。  
  
-   必須先使用產生瀏覽資訊 \(\/FR\) 選項或排除區域變數 \(\/Fr\) 選項建立 PCH，之後使用 PCH 的後續編譯才可以使用這些選項。  
  
## C 7.0\-Compatible \(\/Z7\)  
 如果在 PCH 建立時這個選項生效，則使用 PCH 的後續編譯可使用偵錯資訊。  
  
 如果在建立 PCH 時 C 7.0\-相容 \(\/Z7\) 選項沒有生效，則使用 PCH 和 \/Z7 的後續編譯會觸發警告。  偵錯資訊會置於目前的 .obj 檔中，且偵錯工具無法使用定義於 PCH 的本機符號。  
  
## Include 路徑一致性  
 PCH 並不會包含關於在建立時處於作用中之 Include 路徑的資訊。  當您使用 .pch 檔時，編譯器一律使用現行編譯中指定的 Include 路徑。  
  
## 原始程式檔一致性  
 當您指定使用先行編譯標頭檔 \(\/Yu\) 選項時，編譯器會忽略出現在將被先行編譯之原始程式碼中的所有前置處理器指示詞 \(Preprocessor Directive\) \(包括 Pragma\)。  這種前置處理器指示詞所指定的編譯必須與用於建立先行編譯標頭檔 \(\/Yc\) 選項的編譯相同。  
  
## Pragma 一致性  
 在 PCH 建立期間所處理的 Pragma 通常會影響後續與 PCH 一起使用的檔案。  註解和訊息 Pragma 並不影響編譯的其餘部分。  
  
 下列 Pragma 被保留做為 PCH 一部分，並影響使用 PCH 之編譯的其餘部分。  
  
||||  
|-|-|-|  
|alloc\_text|include\_alias|pack|  
|auto\_inline|init\_seg|pointers\_to\_members|  
|check\_stack|inline\_depth|setlocale|  
|code\_seg|inline\_recursion|vtordisp|  
|data\_seg|intrinsic|warning|  
|function|optimize||  
  
## 請參閱  
 [先行編譯標頭的一致性規則](../../build/reference/precompiled-header-consistency-rules.md)   
 [\/Yu \(使用先行編譯標頭檔\)](../../build/reference/yu-use-precompiled-header-file.md)   
 [編譯器選項](../../build/reference/compiler-options.md)