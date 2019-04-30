---
title: 連結器工具警告 LNK4098
ms.date: 03/26/2019
f1_keywords:
- LNK4098
helpviewer_keywords:
- LNK4098
ms.assetid: 1f1b1408-1316-4e34-80f5-6a02f2db0ac1
ms.openlocfilehash: 66cf1a1bc75405ffc9bae8158bfc8682776a8228
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408091"
---
# <a name="linker-tools-warning-lnk4098"></a>連結器工具警告 LNK4098

> 預設的程式庫 '*程式庫*' je v konfliktu 使用的其他程式庫，請使用 /NODEFAULTLIB:*文件庫*

您嘗試連結不相容的程式庫。

> [!NOTE]
> 執行階段程式庫現在會包含指示詞，以避免混用不同的型別。 在相同的程式中，您會收到此警告，如果您嘗試使用不同的型別或偵錯和非偵錯版本的執行階段程式庫。 例如，如果您編譯一個要使用一種執行階段程式庫的檔案和要使用另一種的另一個檔案 (例如，debug 與零售版) 並嘗試將它們連結，您會收到此警告。 您應該編譯所有原始程式檔，以使用相同的執行階段程式庫。 如需詳細資訊，請參閱 < [/MD、 /MT、 /LD （使用執行階段程式庫）](../../build/reference/md-mt-ld-use-run-time-library.md)編譯器選項。

您可以使用連結器[/verbose: lib](../../build/reference/verbose-print-progress-messages.md)找出哪些文件庫，連結器搜尋的參數。 比方說，當可執行檔使用的多執行緒、 非偵錯執行階段程式庫時，報告的清單應該包含 LIBCMT.lib，且不 LIBCMTD.lib、 MSVCRT.lib 或 MSVCRTD.lib。 您可以告訴連結器使用 忽略不正確的執行階段程式庫[/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)您想要忽略的每個程式庫。

下表顯示您想要根據哪一個執行階段程式庫，應該忽略哪些文件庫。 在命令列上使用其中一個 **/NODEFAULTLIB**要略過的每個程式庫的選項。 在 Visual Studio IDE 中，不同的程式庫，以忽略中的分號分隔**忽略特定的預設程式庫**屬性。

| 使用此執行階段程式庫 | 忽略這些程式庫 |
|-----------------------------------|----------------------------|
| 多執行緒 (libcmt.lib) | msvcrt.lib; libcmtd.lib; msvcrtd.lib |
| 使用 DLL (msvcrt.lib) 的多執行緒 | libcmt.lib; libcmtd.lib; msvcrtd.lib |
| 偵錯多執行緒 (libcmtd.lib) | libcmt.lib; msvcrt.lib; msvcrtd.lib |
| 偵錯多執行緒 DLL (msvcrtd.lib) 的使用 | libcmt.lib; msvcrt.lib; libcmtd.lib |

比方說，如果您收到這則警告，而您想要建立可執行檔使用的執行階段程式庫的非偵錯 DLL 版本，您可以使用連結器中的下列選項：

```cmd
/NODEFAULTLIB:libcmt.lib NODEFAULTLIB:libcmtd.lib /NODEFAULTLIB:msvcrtd.lib
```