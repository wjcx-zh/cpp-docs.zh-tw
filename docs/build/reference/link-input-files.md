---
title: LINK 輸入檔
ms.date: 11/04/2016
helpviewer_keywords:
- files [C++], LINK
- module definition files
- resources [C++], linker files
- LINK tool [C++], input files
- module definition files, linker files
- input files [C++], LINK
- linker [C++], input files
- import libraries [C++], linker files
- command input to linker files [C++]
ms.assetid: bb26fcc5-509a-4620-bc3e-b6c6e603a412
ms.openlocfilehash: aec71d4622821618f377953d36a9676e2233eefc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328195"
---
# <a name="link-input-files"></a>LINK 輸入檔

向連結器提供包含物件、導入和標準庫、資源、模組定義和命令輸入的檔。 LINK 不使用檔案副檔名對文件內容進行假設。 相反,LINK 會檢查每個輸入檔,以確定該檔是哪一類檔。

命令列上的物件檔按照它們在命令列上顯示的順序進行處理。 庫也按命令列順序進行搜索,並帶有以下警告:首先在庫中搜索未解析的符號,然後從命令行和[/DEFAULTLIB(指定預設庫)](defaultlib-specify-default-library.md)指令中搜索以下庫,然後搜索命令行開頭的任何庫。

> [!NOTE]
> LINK 不再接受分號(或任何其他字元)作為回應檔和訂單檔中註釋的開頭。 分號僅識別為模組定義檔 (.def) 中註釋的開始。

LINK 使用以下型態的輸入檔案:

- [.obj 檔案](dot-obj-files-as-linker-input.md)

- [.netmodule 檔案](netmodule-files-as-linker-input.md)

- [.lib 檔案](dot-lib-files-as-linker-input.md)

- [.exp 檔案](dot-exp-files-as-linker-input.md)

- [.def 檔案](dot-def-files-as-linker-input.md)

- [.pdb 檔案](dot-pdb-files-as-linker-input.md)

- [.res 檔案](dot-res-files-as-linker-input.md)

- [.exe 檔案](dot-exe-files-as-linker-input.md)

- [.txt 檔案](dot-txt-files-as-linker-input.md)

- [.ilk 檔案](dot-ilk-files-as-linker-input.md)

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
