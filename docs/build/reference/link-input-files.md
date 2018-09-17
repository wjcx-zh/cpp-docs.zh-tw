---
title: LINK 輸入檔 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- link
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5974914e736278ebb336b6814661845740855fe6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710231"
---
# <a name="link-input-files"></a>LINK 輸入檔

您可以提供連結器和檔案，其中包含物件、 匯入和標準程式庫、 資源、 模組定義，以及輸入的命令。 連結不使用副檔名來進行的檔案內容的相關假設。 相反地，連結會檢查每個輸入的檔案，以判斷它是何種檔案。

在命令列出現的順序會處理命令列上的物件檔案。 程式庫會搜尋命令列的順序，與下列注意事項： 當從程式庫目的檔中將會搜尋該程式庫中第一次，然後下列的程式庫，從命令列和，無法解析的符號[/DEFAULTLIB （指定預設程式庫）](../../build/reference/defaultlib-specify-default-library.md)指示詞，然後將任何命令列開頭的程式庫。

> [!NOTE]
>  連結不再接受以分號 （或任何其他字元），為回應檔和順序檔案中的註解的開頭。 分號僅被視為在模組定義檔 (.def) 的註解的開頭。

連結會使用下列類型的輸入檔：

- [.obj 檔案](../../build/reference/dot-obj-files-as-linker-input.md)

- [.netmodule 檔](../../build/reference/netmodule-files-as-linker-input.md)

- [.lib 檔案](../../build/reference/dot-lib-files-as-linker-input.md)

- [.exp 檔案](../../build/reference/dot-exp-files-as-linker-input.md)

- [.def 檔](../../build/reference/dot-def-files-as-linker-input.md)

- [.pdb 檔案](../../build/reference/dot-pdb-files-as-linker-input.md)

- [.res 檔案](../../build/reference/dot-res-files-as-linker-input.md)

- [.exe 檔案](../../build/reference/dot-exe-files-as-linker-input.md)

- [.txt 檔案](../../build/reference/dot-txt-files-as-linker-input.md)

- [.ilk 檔案](../../build/reference/dot-ilk-files-as-linker-input.md)

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)