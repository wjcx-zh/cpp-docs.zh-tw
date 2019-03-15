---
title: /SYMBOLS
ms.date: 09/05/2018
f1_keywords:
- /symbols
helpviewer_keywords:
- symbols, dumping
- public symbols
- symbols, displaying COFF symbol table
- symbol tables
- SYMBOLS dumpbin option
- /SYMBOLS dumpbin option
- -SYMBOLS dumpbin option
ms.assetid: 34bcae90-4561-4c77-a80c-065508dec39a
ms.openlocfilehash: a47b7da9f0b01353ef15e8b5c070c19e7c521c37
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822544"
---
# <a name="symbols"></a>/SYMBOLS

```
/SYMBOLS
```

此選項會顯示 COFF 符號表。 符號表存在於物件的所有檔案。 只有連結 /debug 映像檔中會顯示 COFF 符號表。

以下是輸出 /SYMBOLS 的描述。 /SYMBOLS 輸出的意義上的其他資訊可在 winnt.h （IMAGE_SYMBOL 和 IMAGE_AUX_SYMBOL） 或 COFF 文件中尋找。

假設下列範例的傾印：

```
Dump of file main.obj
File Type: COFF OBJECT

COFF SYMBOL TABLE
000 00000000 DEBUG    notype       Filename     | .file
    main.cpp
002 000B1FDB ABS      notype       Static       | @comp.id
003 00000000 SECT1    notype       Static       | .drectve
    Section length     26, #relocs    0, #linenums    0, checksum 722C964F
005 00000000 SECT2    notype       Static       | .text
    Section length     23, #relocs    1, #linenums    0, checksum 459FF65F, selection    1 (pick no duplicates)
007 00000000 SECT2    notype ()    External     | _main
008 00000000 UNDEF    notype ()    External     | ?MyDump@@YAXXZ (void __cdecl MyDump(void))

String Table Size = 0x10 bytes

  Summary

         26 .drectve
         23 .text
```

## <a name="remarks"></a>備註

下列描述中，以符號數字開頭的程式碼行說明具有使用者的相關資訊的資料行：

- 第三位數的數字是符號索引/數字。

- 如果第三個資料行包含區段*x*，該區段的目的檔中已定義符號。 但如果 UNDEF 出現時，它不定義在該物件，並必須加以解決，其他地方。

- 第五個資料行 （「 靜態 」、 「 外部 」） 會告知是否該符號會顯示只在該物件中，或是否為公用 (顯示外部)。 靜態符號 _sym 不會連結到公用符號 _sym;這些是兩個名為 _sym 函式的不同執行個體。

編號的行中的最後一欄是符號名稱，兩者裝飾和未裝飾。

只有[/HEADERS](headers.md) DUMPBIN 選項只適用於所產生的檔案上[/GL](gl-whole-program-optimization.md)編譯器選項。

## <a name="see-also"></a>另請參閱

[DUMPBIN 選項](dumpbin-options.md)
