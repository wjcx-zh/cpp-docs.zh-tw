---
title: 連結器工具錯誤 LNK2027 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2027
dev_langs:
- C++
helpviewer_keywords:
- LNK2027
ms.assetid: e2f857a8-8e8a-4697-bbff-12ccb84a35c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 022e363af575e29e3085dcaec21257fa7e4ab5f1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116839"
---
# <a name="linker-tools-error-lnk2027"></a>連結器工具錯誤 LNK2027

無法解析的模組參考 ' module'

傳遞給連結的檔案都以指定在模組上具有相依性 **/ASSEMBLYMODULE**也直接傳遞至連結器。

若要解決 LNK2027，執行下列其中一項動作：

- 請勿傳遞給連結器檔案中包含模組相依性。

- 指定的模組 **/ASSEMBLYMODULE**。

- 如果模組是 safe .netmodule，請直接將模組傳遞給連結器。

如需詳細資訊，請參閱 < [/ASSEMBLYMODULE （將 MSIL 模組加入組件）](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)並[.netmodule 檔作為連結器輸入](../../build/reference/netmodule-files-as-linker-input.md)。