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
ms.openlocfilehash: 25d8e20903a97186e2c32a079fd74ece3626b7fa
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439337"
---
# <a name="link-input-files"></a>LINK 輸入檔

您可以使用包含物件、匯入和標準程式庫、資源、模組定義和命令輸入的檔案來提供連結器。 連結不會使用副檔名來對檔案內容進行假設。 相反地，LINK 會檢查每個輸入檔，以判斷它是哪種檔案。

命令列上的物件檔會依照它們在命令列上出現的順序進行處理。 程式庫也會以命令列順序搜尋，但有下列警告：從程式庫中帶入物件檔案時，無法解析的符號會先在該程式庫中搜尋，然後從命令列和[/DEFAULTLIB （指定預設程式庫）](defaultlib-specify-default-library.md)指示詞，再到命令列開頭的任何程式庫。

> [!NOTE]
>  連結不再接受分號（或任何其他字元）做為回應檔案和順序檔案中的批註開頭。 只有在模組定義檔案（.def）中的批註開始時，才會辨識分號。

連結會使用下列類型的輸入檔：

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
