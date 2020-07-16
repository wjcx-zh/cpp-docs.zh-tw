---
title: 連結器工具錯誤 LNK2038
ms.date: 12/15/2017
f1_keywords:
- LNK2038
helpviewer_keywords:
- LNK2038
ms.openlocfilehash: 69a832716dffee4e024b3bb1a1f0de6ee8105e99
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404160"
---
# <a name="linker-tools-error-lnk2038"></a>連結器工具錯誤 LNK2038

> 偵測到 '*name*' 不相符：值 '*value_1*' 不符合*檔案名 .obj*中的值 '*value_2*'

連結器偵測到符號不相符。 此錯誤表示應用程式的不同部分（包括程式庫或應用程式所連結的其他物件程式碼）會使用衝突的符號定義。 偵測[不相符](../../preprocessor/detect-mismatch.md)的 pragma 是用來定義這類符號，並偵測其衝突的值。

## <a name="possible-causes-and-solutions"></a>可能的原因和解決方案

在專案的目的檔過期時，會發生這個錯誤。 在您嘗試解決這個錯誤的其他方案之前，執行乾淨的組建以確保目的檔是最新的。

Visual Studio 會定義下列符號以防止連結不相容的程式碼，此程式碼可能會造成執行階段錯誤或其他未預期的行為。

- `_MSC_VER`表示用來建立應用程式或程式庫之 Microsoft c + + 編譯器（MSVC）的主要和次要版本號碼。 使用其中一個版本的 MSVC 所編譯的程式碼，與使用具有不同主要和次要版本號碼的版本所編譯的程式碼不相容。 如需詳細資訊，請參閱 `_MSC_VER` [預先定義的宏](../../preprocessor/predefined-macros.md)。

   如果您要連結的程式庫與您所使用的 MSVC 版本不相容，而且無法取得或建立相容版本的程式庫，您可以使用舊版編譯器來建立您的專案：將專案的 [**平臺工具**組] 屬性變更為先前的工具組。 如需詳細資訊，請參閱[如何：修改目標 Framework 和平臺工具](../../build/how-to-modify-the-target-framework-and-platform-toolset.md)組。

- `_ITERATOR_DEBUG_LEVEL`指出 c + + 標準程式庫中已啟用的安全性和偵錯工具功能層級。 這些功能可以變更某些 C++ 標準程式庫物件的表示，因而使它們與使用其他安全性和偵錯功能的項目不相容。 如需詳細資訊，請參閱 [_ITERATOR_DEBUG_LEVEL](../../standard-library/iterator-debug-level.md)。

- `RuntimeLibrary`表示應用程式或程式庫所使用之 c + + 標準程式庫和 C 執行時間的版本。 使用 C++ 標準程式庫或 C 執行階段某個版本的程式碼與使用不同版本的程式碼不相容。 如需詳細資訊，請參閱 [/MD、/MT、/LD (使用執行階段程式庫)](../../build/reference/md-mt-ld-use-run-time-library.md)。

- `_PPLTASKS_WITH_WINRT`表示使用[平行模式程式庫（PPL）](../../parallel/concrt/parallel-patterns-library-ppl.md)的程式碼，會連結至使用[/ZW](../../build/reference/zw-windows-runtime-compilation.md)編譯器選項的不同設定所編譯的物件。 （**/ZW**支援 c + +/cx。）使用或相依于 PPL 的程式碼，必須使用應用程式其餘部分所使用的相同 **/ZW**設定來進行編譯。

請確認這些符號值在您的 Visual Studio 方案的專案中一致，而且它們也與應用程式所連結的程式碼和程式庫一致。

## <a name="third-party-library-issues-and-vcpkg"></a>協力廠商程式庫問題和 vcpkg

如果您在嘗試將協力廠商程式庫設定為組建的一部分時看到此錯誤，請考慮使用 c + + 套件管理員[vcpkg](../../vcpkg.md)來安裝和建立程式庫。 vcpkg 支援大量且不斷成長[的協力廠商程式庫清單](https://github.com/Microsoft/vcpkg/tree/master/ports)，並將成功組建所需的所有設定屬性和相依性設為專案的一部分。

## <a name="see-also"></a>另請參閱

[連結器工具錯誤和警告](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)
