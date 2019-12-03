---
title: 連結器工具警告 LNK4098
description: 描述不相容的程式庫如何使連結器工具警告 LNK4098，以及如何使用/NODEFAULTLIB 來修正此問題。
ms.date: 12/02/2019
f1_keywords:
- LNK4098
helpviewer_keywords:
- LNK4098
ms.assetid: 1f1b1408-1316-4e34-80f5-6a02f2db0ac1
ms.openlocfilehash: 9d0c7da0614651a98d5ed4f3bd3676c7d837ce67
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2019
ms.locfileid: "74682936"
---
# <a name="linker-tools-warning-lnk4098"></a>連結器工具警告 LNK4098

> defaultlib '*library*' 與其他程式庫的使用衝突;使用/NODEFAULTLIB：*library*

您正嘗試連結不相容的媒體櫃。

> [!NOTE]
> 執行時間程式庫現在包含可避免混合不同類型的指示詞。 如果您嘗試在同一個程式中使用不同類型或 debug 和非 debug 版本的執行時間程式庫，將會收到這個警告。 例如，如果您編譯一個檔案來使用一種執行時間程式庫，而另一個檔案使用另一種類型（例如，debug 和 retail）並嘗試連結，您就會收到這個警告。 您應該編譯所有的來源檔案，以使用相同的執行時間程式庫。 如需詳細資訊，請參閱[/md、/mt、/ld （使用執行時間程式庫）](../../build/reference/md-mt-ld-use-run-time-library.md)編譯器選項。

您可以使用連結器的[/verbose： LIB](../../build/reference/verbose-print-progress-messages.md)參數來找出連結器搜尋的程式庫。 例如，當您的可執行檔使用多執行緒、非 debug 執行時間程式庫時，所報告的清單應該包含 LIBCMT.LIB，而不是 LIBCMTD.LIB、MSVCRT.LIB 或 MSVCRTD.LIB。 您可以使用[/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)來指示連結器忽略不正確的執行時間程式庫，以用於您想要忽略的每個媒體櫃。

下表顯示應該忽略哪些程式庫，視您想要使用的執行時間程式庫而定。 在命令列上，針對每個要忽略的程式庫使用一個 **/NODEFAULTLIB**選項。 在 Visual Studio IDE 中，請在 [**忽略特定的預設程式庫**] 屬性中，以分號分隔要忽略的程式庫。

| 使用此執行時間程式庫 | 忽略這些程式庫 |
|-----------------------------------|----------------------------|
| 多執行緒（libcmt.lib .lib） | msvcrt.lib .lib;libcmtd.lib .lib;msvcrtd.lib .lib |
| 使用 DLL 的多執行緒（msvcrt.lib .lib） | libcmt.lib .lib;libcmtd.lib .lib;msvcrtd.lib .lib |
| Debug 多執行緒（libcmtd.lib .lib） | libcmt.lib .lib;msvcrt.lib .lib;msvcrtd.lib .lib |
| 使用 DLL 來進行多執行緒的調試（msvcrtd.lib） | libcmt.lib .lib;msvcrt.lib .lib;libcmtd.lib .lib |

例如，如果您收到此警告，而您想要建立一個可執行檔，而該檔案會使用執行時間程式庫的非偵錯工具 DLL 版本，您可以使用下列選項搭配連結器：

```cmd
/NODEFAULTLIB:libcmt.lib /NODEFAULTLIB:libcmtd.lib /NODEFAULTLIB:msvcrtd.lib
```
