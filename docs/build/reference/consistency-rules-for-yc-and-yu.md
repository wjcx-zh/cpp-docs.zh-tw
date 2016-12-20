---
title: "/Yc 和 /Yu 的一致性規則 | Microsoft Docs"
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
  - "/yc"
  - "/yu"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Yc 編譯器選項 [C++]"
  - "/Yu 編譯器選項 [C++]"
  - "Yc 編譯器選項 [C++]"
  - "-Yc 編譯器選項 [C++]"
  - "Yu 編譯器選項 [C++]"
  - "-Yu 編譯器選項 [C++]"
ms.assetid: 9dfb0e32-ec9b-4a36-9355-27a0e5fba512
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Yc 和 /Yu 的一致性規則
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

當您使用以 \/Yc 或 \/Yu 所建立的先行編譯標頭時，編譯器會將現行編譯環境與您建立 .pch 檔時存在的環境做比較。  請務必對現行編譯指定一個與前一個環境一致的環境 \(使用一致的編譯器選項、Pragma 等等\)。  如果編譯器偵測到不一致，它會發出警告並識別可能的不一致之處。  這種警告並不一定指示 .pch 檔的問題；它們只是警告您可能的衝突。  下列章節說明先行編譯標頭的一致性需求。  
  
## 編譯器選項一致性  
 下表列出在使用先行編譯標頭時可能觸發不一致警告的編譯器選項。  
  
|選項|Name|規則|  
|--------|----------|--------|  
|\/D|定義常數和巨集|在建立先行編譯標頭的編譯與現行編譯之間必須相同。  並不會檢查已定義常數的狀態，但若是您的檔案相依於變更常數的值，則可能發生無法預期的結果。|  
|\/E 或 \/EP|複製前置處理器輸出至標準輸出|先行編譯標頭不適用於 \/E 或 \/EP 選項。|  
|\/Fr 或 \/FR|產生 Microsoft 來源瀏覽器資訊|若要讓 \/Fr 和 \/FR 選項隨 \/Yu 選項有效，它們在先行編譯標頭建立時必須也生效。  使用先行編譯標頭的後續編譯也會產生來源瀏覽器資訊。  瀏覽器資訊置於一個單一的 .sbr 檔中，並由其他檔案以參考 CodeView 資訊的相同方式所參考。  您無法覆寫來源瀏覽器資訊的位置。|  
|\/GA、\/GD、\/GE、\/Gw 或 \/GW|Windows 通訊協定選項|在建立先行編譯標頭的編譯與現行編譯之間必須相同。  如果這些選項有異，即產生警告訊息。|  
|\/Zi|產生完整偵錯資訊|如果在先行編譯標頭建立時這個選項生效，則使用該先行編譯的後續編譯可使用該偵錯資訊。  如果先行編譯標頭建立時 \/Zi 沒有生效，則使用先行編譯和 \/Zi 選項的後續編譯會觸發警告。  偵錯資訊會置於目前的目的檔中，且偵錯工具無法使用定義於先行編譯標頭的本機符號。|  
  
> [!NOTE]
>  先行編譯標頭功能只適用於 C 和 C\+\+ 原始程式檔的檔案。  
  
## Include 路徑一致性  
 以 \/Yc 建立的先行編譯標頭並不包含關於在建立 .pch 檔時生效的 Include 路徑之資訊。  當您使用 .pch 檔時，編譯器一律使用現行編譯中指定的 Include 路徑。  
  
## 原始程式檔一致性  
 當您使用先行編譯標頭時，編譯器會忽略所有出現在 hdrstop Pragma 之前的前置處理器指示詞 \(包括 Pragma\)。  這種前置處理器指示詞所指定的編譯必須與用來建立先行編譯標頭檔的編譯相同。  
  
## Pragma 一致性  
 在先行編譯標頭的編譯期間所處理的 Pragma，通常會影響在其中後續使用先行編譯標頭的檔案。  下列 Pragma 只影響 .pch 檔內的程式碼；它們並不會影響後來使用 .pch 檔的程式碼：  
  
||||  
|-|-|-|  
|Comment|page|subtitle|  
|Linesize|pagesize|標題|  
|Message|skip||  
  
 下列 Pragma 被保留做為先行編譯標頭的一部分，並影響使用先行編譯標頭之編譯的其餘部分：  
  
||||  
|-|-|-|  
|alloc\_text|function|optimize|  
|auto\_inline|inline\_depth|Pack|  
|check\_pointer|inline\_recursion|same\_seg|  
|check\_stack|intrinsic|warning|  
|code\_seg|loop\_opt||  
|data\_seg|native\_caller||  
  
## 請參閱  
 [先行編譯標頭的一致性規則](../../build/reference/precompiled-header-consistency-rules.md)   
 [\/Yc \(建立先行編譯標頭檔\)](../../build/reference/yc-create-precompiled-header-file.md)   
 [\/Yu \(使用先行編譯標頭檔\)](../../build/reference/yu-use-precompiled-header-file.md)