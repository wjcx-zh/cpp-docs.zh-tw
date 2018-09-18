---
title: 連結器工具錯誤 LNK1302 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1302
dev_langs:
- C++
helpviewer_keywords:
- LNK1302
ms.assetid: aea3c753-c2c4-4249-bbc3-f2d4f0164b5e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3dc85b37d58e12602c02c2207c1f38bda9344e59
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045506"
---
# <a name="linker-tools-error-lnk1302"></a>連結器工具錯誤 LNK1302

僅支援連結 safe .netmodule，無法連結 .netmodule 檔

.Netmodule (以編譯 **/LN**) 傳遞給連結器中的使用者嘗試叫用 MSIL 連結。  C + + 模組是 MSIL 連結編譯時的有效值 **/clr: safe**。

若要更正這個錯誤，以編譯 **/clr: safe**若要啟用 MSIL 連結，或傳遞 **/clr**或 **/clr: pure** .obj 檔給連結器，而不是模組。

如需詳細資訊，請參閱

- [/LN (建立 MSIL 模組)](../../build/reference/ln-create-msil-module.md)

- [.netmodule 檔作為連結器輸入](../../build/reference/netmodule-files-as-linker-input.md)