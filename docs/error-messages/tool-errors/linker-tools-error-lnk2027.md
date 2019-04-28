---
title: 連結器工具錯誤 LNK2027
ms.date: 11/04/2016
f1_keywords:
- LNK2027
helpviewer_keywords:
- LNK2027
ms.assetid: e2f857a8-8e8a-4697-bbff-12ccb84a35c1
ms.openlocfilehash: e74912780bab3056ead36ae3705f0910805228e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62299006"
---
# <a name="linker-tools-error-lnk2027"></a>連結器工具錯誤 LNK2027

無法解析的模組參考 ' module'

傳遞給連結的檔案都以指定在模組上具有相依性 **/ASSEMBLYMODULE**也直接傳遞至連結器。

若要解決 LNK2027，執行下列其中一項動作：

- 請勿傳遞給連結器檔案中包含模組相依性。

- 指定的模組 **/ASSEMBLYMODULE**。

- 如果模組是 safe .netmodule，請直接將模組傳遞給連結器。

如需詳細資訊，請參閱 < [/ASSEMBLYMODULE （將 MSIL 模組加入組件）](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)並[.netmodule 檔作為連結器輸入](../../build/reference/netmodule-files-as-linker-input.md)。