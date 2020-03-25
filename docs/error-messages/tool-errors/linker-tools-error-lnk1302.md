---
title: 連結器工具錯誤 LNK1302
ms.date: 11/04/2016
f1_keywords:
- LNK1302
helpviewer_keywords:
- LNK1302
ms.assetid: aea3c753-c2c4-4249-bbc3-f2d4f0164b5e
ms.openlocfilehash: 8323fa234851ce3ba12083adb74d5ee0fba0ac69
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194924"
---
# <a name="linker-tools-error-lnk1302"></a>連結器工具錯誤 LNK1302

僅支援連結 safe .netmodule，無法連結 .netmodule 檔

在使用者嘗試叫用 MSIL 連結時，將 .netmodule （以 **/LN**編譯）傳遞給連結器。  如果C++模組是以 **/clr： safe**編譯，則它適用于 MSIL 連結。

若要更正這個錯誤，請使用 **/clr： safe**進行編譯以啟用 MSIL 連結，或將 **/clr**或 **/clr： pure**檔案傳遞至連結器，而不是模組。

如需相關資訊，請參閱

- [/LN (建立 MSIL 模組)](../../build/reference/ln-create-msil-module.md)

- [.netmodule 檔作為連結器輸入](../../build/reference/netmodule-files-as-linker-input.md)
