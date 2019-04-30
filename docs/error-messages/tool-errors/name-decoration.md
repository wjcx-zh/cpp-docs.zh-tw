---
title: 名稱裝飾
ms.date: 04/22/2019
helpviewer_keywords:
- name decoration [C++]
- names [C++], decorated
- decorated names, calling conventions
ms.assetid: 8327a27b-bb4f-49f2-8218-b851b9d2a463
ms.openlocfilehash: d1557f53a07a544ff4f9e5a63f905e6854fb74ce
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393151"
---
# <a name="name-decoration"></a>名稱裝飾

名稱裝飾通常指的是 C++ 命名慣例，但也可以套用到一些 C 的案例。 根據預設，C++ 會使用函式名稱、參數和傳回類型來建立函式的連結器名稱。 請考慮下列函式宣告：

`void CALLTYPE test(void);`

下表顯示各種呼叫慣例的連結器名稱。

|呼叫慣例|`extern "C"` 或`.c`檔案|`.cpp``.cxx`或 `/TP`|
|------------------------|---------------------------|------------------------|
|C 命名慣例 (`__cdecl`)|`_test`|`?test@@ZAXXZ`|
|快速呼叫命名慣例 (`__fastcall`)|`@test@0`|`?test@@YIXXZ`|
|標準呼叫命名慣例 (`__stdcall`)|`_test@0`|`?test@@YGXXZ`|
|向量呼叫命名慣例 (`__vectorcall`)|`test@@0`|`?test@@YQXXZ`|

使用`extern "C"`呼叫 C 函式，從C++。 `extern "C"` 會強制使用 C 命名慣例的非類別C++函式。 注意編譯器參數 **/Tc**或是 **/Tp**，這會告訴編譯器忽略副檔名，並將檔案編譯為 C 或C++，分別。 這些選項可能會導致未預期的連結器名稱。

參數不相符的函式原型也可能導致這個錯誤。 名稱裝飾會將函式的參數納入最終的裝飾函式名稱。 不符合那些在函式宣告的參數類型來呼叫函式也可能造成 LNK2001。

目前沒有任何標準的C++命名編譯器廠商或不同的編譯器版本之間。 連結其他編譯器所編譯的物件檔案可能不會產生相同的命名配置，並可能會導致無法解析的外部符號。

## <a name="see-also"></a>另請參閱

[連結器工具錯誤 LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md)