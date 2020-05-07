---
title: 建立發行組建時的常見問題
ms.date: 11/04/2016
helpviewer_keywords:
- unexpected code generation
- debugging [MFC], release builds
- release builds, troubleshooting
- stray pointers
- debug builds, difference from release builds
- MFC [C++], release builds
- heap layout problems
- pointers, stray
- release builds, building applications
- debug memory allocator
- optimization [C++], compiler
- projects [C++], debug configuration
- troubleshooting release builds
- memory [C++], overwrites
ms.assetid: 73cbc1f9-3e33-472d-9880-39a8e9977b95
ms.openlocfilehash: 9bd1cafe40417872d42f2e9e1427e5f2eccad7a7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328858"
---
# <a name="common-problems-when-creating-a-release-build"></a>建立發行組建時的常見問題

在開發期間，您通常會使用專案的「偵錯工具」組建來建立和測試。 如果您接著建立發行組建的應用程式，您可能會收到存取違規。

下列清單顯示 debug 和 release （nondebug）組建之間的主要差異。 還有其他差異，但以下是在發行組建中運作時，會導致應用程式在版本建立中失敗的主要差異。

- [堆積版面配置](#_core_heap_layout)

- [編譯](#_core_compilation)

- [指標支援](#_core_pointer_support)

- [最佳化](#_core_optimizations)

如需如何在 debug 組建中捕捉發行組建錯誤的詳細資訊，請參閱[/GZ （在 Debug build 中捕捉發行組建錯誤）](reference/gz-enable-stack-frame-run-time-error-checking.md)編譯器選項。

## <a name="heap-layout"></a><a name="_core_heap_layout"></a>堆積版面配置

當應用程式在 debug （但不是發行）中運作時，堆積配置會造成大約90% 的明顯問題。

當您建立用於 debug 的專案時，您會使用「偵錯工具記憶體配置器」。 這表示所有記憶體配置都有防護位元組放在它們的周圍。 這些防護位元組會偵測到記憶體的覆寫。 因為發行和 debug 版本之間的堆積配置不同，所以記憶體覆寫可能不會在 debug 組建中建立任何問題，但可能會在發行組建中產生重大影響。

如需詳細資訊，請參閱[檢查記憶體覆寫](checking-for-memory-overwrites.md)和[使用 Debug Build 來檢查記憶體是否覆寫](using-the-debug-build-to-check-for-memory-overwrite.md)。

## <a name="compilation"></a><a name="_core_compilation"></a>編譯

當您建立發行時，許多 MFC 宏和大部分的 MFC 執行都會變更。 特別是，ASSERT 宏在發行組建中會評估為任何內容，因此不會執行任何在判斷提示中找到的程式碼。 如需詳細資訊，請參閱[檢查 ASSERT 語句](using-verify-instead-of-assert.md)。

某些函式會內嵌在發行組建中，以提高速度。 優化通常會在發行組建中開啟。 也會使用不同的記憶體配置器。

## <a name="pointer-support"></a><a name="_core_pointer_support"></a>指標支援

缺少偵錯工具資訊會將填補從您的應用程式中移除。 在發行組建中，偏離的指標有更高的機會指向未初始化的記憶體，而不是指向 debug 資訊。

## <a name="optimizations"></a><a name="_core_optimizations"></a>優化

根據特定程式碼片段的本質而定，優化編譯器可能會產生非預期的程式碼。 這是發行組建問題的最不可能原因，但有時會發生這種情況。 如需解決方案，請參閱[優化您的程式碼](optimizing-your-code.md)。

## <a name="see-also"></a>請參閱

[發行組建](release-builds.md)<br/>
[解決發行組建的問題](fixing-release-build-problems.md)
