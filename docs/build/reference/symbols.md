---
title: "-SYMBOLS |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /symbols
dev_langs: C++
helpviewer_keywords:
- symbols, dumping
- public symbols
- symbols, displaying COFF symbol table
- symbol tables
- SYMBOLS dumpbin option
- /SYMBOLS dumpbin option
- -SYMBOLS dumpbin option
ms.assetid: 34bcae90-4561-4c77-a80c-065508dec39a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 360f26de5043eae7f5cdb4688612f95b96be8fbd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="symbols"></a>/SYMBOLS
```  
/SYMBOLS  
```  
  
 此選項會顯示 COFF 符號表。 符號表存在於所有目的檔中。 COFF 符號表中才會出現映像檔使用 /debug 進行連結。  
  
 下列是輸出 /SYMBOLS 的描述。 在 winnt.h （IMAGE_SYMBOL 和 IMAGE_AUX_SYMBOL） 或 COFF 文件中尋找找 /SYMBOLS 輸出的意義上的其他資訊。  
  
 假設下列範例的傾印：  
  
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
  
## <a name="remarks"></a>備註  
 下列說明，以符號數字開頭的程式碼行說明具有使用者的相關資訊的資料行：  
  
-   第三個位數的數字是符號索引/編號。  
  
-   如果第三個資料行包含區段*x*，該區段的目的檔中定義的符號。 但是如果出現 UNDEF，該物件中未定義，必須先解決其他位置。  
  
-   第五個資料行 （「 靜態 」、 「 外部 」） 會告知符號是否顯示只在該物件，或是否為公用 (可見外部)。 靜態符號 _sym 不會連結到公用符號 _sym;這些是兩個名為 _sym 函式的不同執行個體。  
  
 編號的行中的最後一個資料行的符號名稱，兩者裝飾和未裝飾。  
  
 只有[/HEADERS](../../build/reference/headers.md) DUMPBIN 選項僅適用於所產生的檔案上[/GL](../../build/reference/gl-whole-program-optimization.md)編譯器選項。  
  
## <a name="see-also"></a>另請參閱  
 [DUMPBIN 選項](../../build/reference/dumpbin-options.md)