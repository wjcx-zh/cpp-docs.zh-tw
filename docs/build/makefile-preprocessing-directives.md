---
title: "Makefile 前置處理指示詞 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "!UNDEF"
  - "!INCLUDE"
  - "!IFNDEF"
  - "!MESSAGE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "!CMDSWITCHES 指示詞"
  - "!ELSE 指示詞"
  - "!ELSEIF 指示詞"
  - "!ELSEIFDEF 指示詞"
  - "!ELSEIFNDEF 指示詞"
  - "!ENDIF 指示詞"
  - "!ERROR 指示詞"
  - "!IF 指示詞"
  - "!IFDEF 指示詞"
  - "!IFNDEF 指示詞"
  - "!INCLUDE 指示詞"
  - "!MESSAGE 指示詞"
  - "!UNDEF 指示詞"
  - "CMDSWITCHES 指示詞"
  - "指示詞, Makefile 前置處理"
  - "ELSE 指示詞"
  - "ELSEIF 指示詞"
  - "ELSEIFDEF 指示詞"
  - "ELSEIFNDEF 指示詞"
  - "ENDIF 指示詞"
  - "ERROR 指示詞"
  - "IF 指示詞"
  - "IFDEF 指示詞"
  - "IFNDEF 指示詞"
  - "INCLUDE 指示詞"
  - "Makefile, 前置處理器指示詞"
  - "MESSAGE 指示詞"
  - "NMAKE 程式, 運算式"
  - "NMAKE 程式, 前置處理器指示詞"
  - "前置處理器指示詞, Makefile"
  - "UNDEF 指示詞"
ms.assetid: bcedeccb-d981-469d-b9e8-ab5d097fd8c2
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Makefile 前置處理指示詞
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

前置處理指示詞不區分大小寫。  初始驚嘆號 \(\!\) 必須出現在行的開頭。  零個或多個空格或定位字元可以出現在驚歎號之後，表示縮排。  
  
 **\!CMDSWITCHES**  
 {**\+**&#124;**–**}*選項*...  開啟或關閉所列出的每個 *option*。  空格或定位字元必須要出現在 \+ 或 – 運算子之前，兩者都不能出現在運算子和[選項字母](../build/nmake-options.md)之間。  字母不區分大小寫，且沒有使用斜線 \( \/ \) 指定。  若要開啟某些選項並關閉其他選項，請使用不同的 **\!CMDSWITCHES** 規格。  
  
 在 Makefile 中只能使用 \/D、\/I、\/N 和 \/S。  在 Tools.ini 中，除了 \/F、\/HELP、\/NOLOGO、\/X 和 \/? 以外，其他所有選項都可以使用。  在描述區塊中所指定的變更，要等到下一個描述區塊時才會生效。  這個指示詞更新 **MAKEFLAGS**，如果指定了 **MAKEFLAGS**，在遞迴期間就會繼承變更。  
  
 **\!ERROR**  *text*  
 在錯誤 U1050 中顯示 *text*，然後暫止 NMAKE \(即使使用了 \/K、\/I、**.IGNORE**、**\!CMDSWITCHES** 或破折號 \(–\) 命令修飾詞\)。  會忽略在 *text* 之前的空格或定位字元。  
  
 **\!MESSAGE**  *text*  
 顯示 *text* 到標準輸出裝置。  會忽略在 *text* 之前的空格或定位字元。  
  
 **\!INCLUDE**\[ **\<**\] *filename*\[ **\>**\]  
 以 Makefile 形式讀取 *filename*，然後繼續使用目前的 Makefile。  NMAKE 首先在指定或目前目錄中搜尋 *filename*，接著遞迴地搜尋任何 Makefile 的父目錄，然後如果 *filename* 是放置在角括弧 \(\< \>\) 內，就會搜尋 **INCLUDE** 巨集所指定的目錄，此巨集最初設定為 INCLUDE 環境變數。  將 **.SUFFIXES** 設定、**.PRECIOUS** 和推斷規則 \(Inference Rule\) 傳遞至遞迴的 Makefile，將會相當有用的。  
  
 **\!IF**  `constantexpression`  
 如果 `constantexpression` 評估為非零的值，就會處理在 **\!IF** 和下一個 **\!ELSE** 或 `!ENDIF` 之間的陳述式。  
  
 **\!IFDEF**  *macroname*  
 如果定義了 *macroname*，就會處理在 `!IFDEF` 和下一個 **\!ELSE** 或 `!ENDIF` 之間的陳述式。  必須要定義 null 巨集。  
  
 **\!IFNDEF**  *macroname*  
 如果未定義 *macroname*，就會處理在 **\!IFNDEF** 和下一個 **\!ELSE** 或 `!ENDIF` 之間的陳述式。  
  
 **\!ELSE**\[**IF** *constantexpression* &#124; **IFDEF** *macroname*&#124; **IFNDEF** *macroname*\]  
 如果之前的 **\!IF**、`!IFDEF` 或 **\!IFNDEF** 陳述式評估為零，就會處理在 **\!ELSE** 和下一個 `!ENDIF` 之間的陳述式。  選擇性關鍵字可以讓使用者更進一步地控制前置處理。  
  
 **\!ELSEIF**  
 **\!ELSE IF** 的同義資料表 \(Synonym\)。  
  
 **\!ELSEIFDEF**  
 **\!ELSE IFDEF** 的同義資料表。  
  
 **\!ELSEIFNDEF**  
 **\!ELSE IFNDEF** 的同義資料表。  
  
 `!ENDIF`  
 標記 **\!IF**、`!IFDEF` 或 **\!IFNDEF** 區塊的結尾。  會忽略在同一行上 `!ENDIF` 之後的任何文字。  
  
 **\!UNDEF**  *macroname*  
 取消定義 *macroname*。  
  
## 請參閱  
 [Makefile 前置處理](../build/makefile-preprocessing.md)