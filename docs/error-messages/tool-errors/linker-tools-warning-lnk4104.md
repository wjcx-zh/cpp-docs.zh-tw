---
title: 連結器工具警告 LNK4104
ms.date: 11/04/2016
f1_keywords:
- LNK4104
helpviewer_keywords:
- LNK4104
ms.assetid: ca6728db-d616-419a-a570-65e8445c6079
ms.openlocfilehash: 604dccf01b3dffc0060546bebf19d64c16ebf965
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193962"
---
# <a name="linker-tools-warning-lnk4104"></a>連結器工具警告 LNK4104

符號 ' symbol ' 的匯出應為私用

`symbol` 可以是下列其中一項：

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

當您建立 DLL 的匯入程式庫並匯出上述其中一個函式，但未在模組定義檔中將它指定為私用時，就會發出此警告。 一般而言，這些函式只會匯出供 OLE 使用。 將它們放在匯入程式庫時，可能會導致不尋常的行為，因為連結至程式庫的程式不正確地呼叫它們。 如需私用關鍵字的詳細資訊，請參閱[匯出](../../build/reference/exports.md)。
