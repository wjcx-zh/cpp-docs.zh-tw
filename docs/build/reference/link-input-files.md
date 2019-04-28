---
title: LINK 輸入檔
ms.date: 11/04/2016
f1_keywords:
- link
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
ms.openlocfilehash: 48ad9423ae35c22a97a873fe6a2a0479c12ab33b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291505"
---
# <a name="link-input-files"></a>LINK 輸入檔

您可以提供連結器和檔案，其中包含物件、 匯入和標準程式庫、 資源、 模組定義，以及輸入的命令。 連結不使用副檔名來進行的檔案內容的相關假設。 相反地，連結會檢查每個輸入的檔案，以判斷它是何種檔案。

在命令列出現的順序會處理命令列上的物件檔案。 命令列的順序，會搜尋程式庫，與下列注意事項：當從程式庫目的檔中將會搜尋該程式庫中第一次，然後從命令列的下列程式庫，無法解析的符號，並[/DEFAULTLIB （指定預設程式庫）](defaultlib-specify-default-library.md)指示詞，然後在命令列開頭的任何程式庫。

> [!NOTE]
>  連結不再接受以分號 （或任何其他字元），為回應檔和順序檔案中的註解的開頭。 分號僅被視為在模組定義檔 (.def) 的註解的開頭。

連結會使用下列類型的輸入檔：

- [.obj 檔案](dot-obj-files-as-linker-input.md)

- [.netmodule 檔](netmodule-files-as-linker-input.md)

- [.lib 檔案](dot-lib-files-as-linker-input.md)

- [.exp 檔案](dot-exp-files-as-linker-input.md)

- [.def 檔](dot-def-files-as-linker-input.md)

- [.pdb files](dot-pdb-files-as-linker-input.md)

- [.res 檔案](dot-res-files-as-linker-input.md)

- [.exe 檔案](dot-exe-files-as-linker-input.md)

- [.txt 檔案](dot-txt-files-as-linker-input.md)

- [.ilk 檔案](dot-ilk-files-as-linker-input.md)

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
