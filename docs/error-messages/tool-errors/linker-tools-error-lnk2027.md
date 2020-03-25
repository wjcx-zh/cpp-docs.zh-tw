---
title: 連結器工具錯誤 LNK2027
ms.date: 11/04/2016
f1_keywords:
- LNK2027
helpviewer_keywords:
- LNK2027
ms.assetid: e2f857a8-8e8a-4697-bbff-12ccb84a35c1
ms.openlocfilehash: 0c531f70f98a017e8b75cceddc684f99d33bc554
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194588"
---
# <a name="linker-tools-error-lnk2027"></a>連結器工具錯誤 LNK2027

無法解析的模組參考 ' module '

傳遞至連結器的檔案相依于不是以 **/ASSEMBLYMODULE**指定的模組，也不會直接傳遞至連結器。

若要解決 LNK2027，請執行下列其中一項動作：

- 請勿將具有模組相依性的檔案傳遞至連結器。

- 使用 **/ASSEMBLYMODULE**指定模組。

- 如果模組是 safe .netmodule，請直接將模組傳遞給連結器。

如需詳細資訊，請參閱[/ASSEMBLYMODULE （將 MSIL 模組新增至元件）](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)和[.netmodule 檔案做為連結器輸入](../../build/reference/netmodule-files-as-linker-input.md)。
