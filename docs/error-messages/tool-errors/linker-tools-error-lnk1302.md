---
title: 連結器工具錯誤 LNK1302
ms.date: 11/04/2016
f1_keywords:
- LNK1302
helpviewer_keywords:
- LNK1302
ms.assetid: aea3c753-c2c4-4249-bbc3-f2d4f0164b5e
ms.openlocfilehash: c3b1117b31db4759b385943323a581da7a58f0c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160441"
---
# <a name="linker-tools-error-lnk1302"></a>連結器工具錯誤 LNK1302

僅支援連結 safe .netmodule，無法連結 .netmodule 檔

.Netmodule (以編譯 **/LN**) 傳遞給連結器中的使用者嘗試叫用 MSIL 連結。  C++模組是 MSIL 連結編譯時的有效值 **/clr: safe**。

若要更正這個錯誤，以編譯 **/clr: safe**若要啟用 MSIL 連結，或傳遞 **/clr**或 **/clr: pure** .obj 檔給連結器，而不是模組。

如需詳細資訊，請參閱

- [/LN (建立 MSIL 模組)](../../build/reference/ln-create-msil-module.md)

- [.netmodule 檔作為連結器輸入](../../build/reference/netmodule-files-as-linker-input.md)