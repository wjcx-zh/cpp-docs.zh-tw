---
title: "/SYMBOLS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/symbols"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/SYMBOLS dumpbin 選項"
  - "公用符號"
  - "符號表"
  - "SYMBOLS dumpbin 選項"
  - "-SYMBOLS dumpbin 選項"
  - "符號, 顯示 COFF 符號表"
  - "符號, 傾印"
ms.assetid: 34bcae90-4561-4c77-a80c-065508dec39a
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# /SYMBOLS
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/SYMBOLS  
```  
  
 這個選項顯示 COFF 符號表。  所有的目的檔中都有符號表存在。  COFF 符號表只有在使用 \/DEBUG 連結時才會出現在影像檔中。  
  
 以下是 \/SYMBOLS 輸出的說明。  如需 \/SYMBOLS 輸出之意義的其他資訊，請參閱 winnt.h \(IMAGE\_SYMBOL 和 IMAGE\_AUX\_SYMBOL\) 或 COFF 文件。  
  
 進行下列範例傾印：  
  
```  
Dump of file main.obj  
File Type: COFF OBJECT  
  
COFF    SYMBOL    TABLE  
000    00000000   DEBUG      notype      Filename      | .file  
      main.cpp  
002   000B1FDB   ABS      notype      Static      | @comp.id  
003   00000000   SECT1      notype      Static      | .drectve  
      Section length       26, #relocs   0, #linenums    0, checksum 722C964F  
005   00000000   SECT2      notype      Static      | .text  
      Section length      23, #relocs      1, #linenums    0, checksum 459FF65F, selection    1 (pick no duplicates)  
007   00000000   SECT2      notype ()   External      | _main  
008   00000000   UNDEF      notype ()   External      | ?MyDump@@YAXXZ (void __cdecl MyDump(void))  
  
String Table Size = 0x10 bytes  
  
Summary  
  
      26 .drectve  
      23 .text  
```  
  
## 備註  
 以下內容 \(針對以符號編號開頭的程式碼行\) 說明載有使用者相關資訊的直欄：  
  
-   第一組三位數數字是符號索引 \/ 編號。  
  
-   如果第三個資料行包含 SECT*x*，則表示該符號是定義於目的檔中的該區段。  但如果出現 UNDEF，則表示它不是在該物件中定義，必須在其他處另行解析。  
  
-   第五個直欄 \(Static、External\) 表示該符號是只能在該物件內看到或是它是公用符號 \(在外部可見\)。  靜態符號 \_sym 將不會連結到公用符號 \_sym；這些是名稱為 \_sym 之函式的兩個不同的執行個體。  
  
 在具編號的行中，最後一個直欄是裝飾 \(Decorated\) 和未裝飾 \(Undecorated\) 的符號名稱。  
  
 只有 [\/HEADERS](../../build/reference/headers.md) DUMPBIN 選項可用在以 [\/GL](../../build/reference/gl-whole-program-optimization.md) 編譯器選項所產生的檔案上。  
  
## 請參閱  
 [DUMPBIN 選項](../../build/reference/dumpbin-options.md)