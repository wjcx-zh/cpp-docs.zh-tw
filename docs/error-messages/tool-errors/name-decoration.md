---
title: 名稱裝飾
ms.date: 04/22/2019
helpviewer_keywords:
- name decoration [C++]
- names [C++], decorated
- decorated names, calling conventions
ms.assetid: 8327a27b-bb4f-49f2-8218-b851b9d2a463
ms.openlocfilehash: cc00c971eac2a089ccec5bd9eab594bdf4e8348e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173513"
---
# <a name="name-decoration"></a>名稱裝飾

名稱裝飾通常指的是 C++ 命名慣例，但也可以套用到一些 C 的案例。 根據預設，C++ 會使用函式名稱、參數和傳回類型來建立函式的連結器名稱。 請考慮下列函式宣告：

`void CALLTYPE test(void);`

下表顯示各種呼叫慣例的連結器名稱。

|呼叫慣例|`extern "C"` 或 `.c` 檔案|`.cpp`、`.cxx` 或 `/TP`|
|------------------------|---------------------------|------------------------|
|C 命名慣例 (`__cdecl`)|`_test`|`?test@@ZAXXZ`|
|快速呼叫命名慣例（`__fastcall`）|`@test@0`|`?test@@YIXXZ`|
|標準呼叫命名慣例（`__stdcall`）|`_test@0`|`?test@@YGXXZ`|
|向量呼叫命名慣例（`__vectorcall`）|`test@@0`|`?test@@YQXXZ`|

使用 `extern "C"` 從C++呼叫 C 函式。 `extern "C"` 強制使用非類別C++函式的 C 命名慣例。 請注意編譯器參數 **/tc**或 **/tp**，這會告訴編譯器忽略副檔名，並分別將檔案編譯為 C 或C++。 這些選項可能會導致您不預期的連結器名稱。

參數不相符的函式原型也可能導致這個錯誤。 名稱裝飾會將函式的參數納入最終的裝飾函式名稱。 呼叫具有不符合函式宣告中參數類型的函式時，可能也會造成 LNK2001。

在編譯器廠商之間，或C++甚至是不同版本的編譯器之間，目前沒有任何標準可進行命名。 連結由其他編譯器所編譯的物件檔可能不會產生相同的命名配置，而可能導致無法解析的外部。

## <a name="see-also"></a>另請參閱

[連結器工具錯誤 LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md)
