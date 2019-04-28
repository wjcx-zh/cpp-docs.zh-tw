---
title: 連結器工具警告 LNK4104
ms.date: 11/04/2016
f1_keywords:
- LNK4104
helpviewer_keywords:
- LNK4104
ms.assetid: ca6728db-d616-419a-a570-65e8445c6079
ms.openlocfilehash: 3d89b27c32b33b917abb7fc140eebf5924142423
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298538"
---
# <a name="linker-tools-warning-lnk4104"></a>連結器工具警告 LNK4104

符號 'symbol' 的匯出應為 PRIVATE

`symbol`可以是下列其中之一：

- `DllCanUnloadNow`

- `DllGetClassObject`

- `DllGetClassFactoryFromClassString`

- `DllGetDocumentation`

- `DllInitialize`

- `DllInstall`

- `DllRegisterServer`

- `DllRegisterServerEx`

- `DllRegisterServerExW`

- `DllUnload`

- `DllUnregisterServer`

- `RasCustomDeleteEntryNotify`

- `RasCustomDial`

- `RasCustomDialDlg`

- `RasCustomEntryDlg`

當您在建立匯入程式庫的 dll，就會發出這個警告，而且匯出其中一個以上的函式而不指定它為私用模組定義檔中的。 一般情況下，這些函式會使用匯出只能由 OLE。 將它們放在匯入程式庫時可能會導致不尋常的行為不正確地連結至程式庫的程式會對其進行呼叫。 如需私用的關鍵字的詳細資訊，請參閱[匯出](../../build/reference/exports.md)。