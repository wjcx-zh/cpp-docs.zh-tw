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

在開發過程中,您通常會使用專案的調試生成生成和測試。 如果隨後為發佈生成構建應用程式,則可能會收到訪問衝突。

下面的清單顯示了調試和發佈(非調試)生成之間的主要區別。 還有其他差異,但以下是導致應用程式在調試生成中工作時在發佈版本中失敗的主要區別。

- [堆佈局](#_core_heap_layout)

- [編譯](#_core_compilation)

- [指標支援](#_core_pointer_support)

- [最佳化](#_core_optimizations)

有關如何捕獲調試生成中的發佈生成錯誤的資訊,請參閱[/GZ(調試生成中的捕獲發佈-生成錯誤)](reference/gz-enable-stack-frame-run-time-error-checking.md)編譯器選項。

## <a name="heap-layout"></a><a name="_core_heap_layout"></a>堆佈局

當應用程式在調試中工作時,堆佈局將是大約 90% 的明顯問題的原因,但不會釋放。

生成項目進行調試時,將使用調試記憶體分配器。 這意味著所有內存分配都位於它們周圍。 這些保護位元組檢測到記憶體覆蓋。 由於堆佈局在版本和調試版本之間不同,因此記憶體覆蓋可能不會在調試生成中造成任何問題,但在發佈版本中可能具有災難性影響。

有關詳細資訊,請參閱[檢查記憶體覆蓋](checking-for-memory-overwrites.md),並使用[除錯產生檢查記憶體覆蓋](using-the-debug-build-to-check-for-memory-overwrite.md)。

## <a name="compilation"></a><a name="_core_compilation"></a>編譯

許多 MFC 宏和大部分 MFC 實現在生成以進行發佈時會發生變化。 特別是,ASSERT 宏在發佈版本中不計算任何內容,因此不會執行 ASSERT 中找到的代碼。 有關詳細資訊,請參閱檢查[ASSERT 語句](using-verify-instead-of-assert.md)。

某些函數內聯在版本版本中提高了速度。 優化通常在發佈版本中打開。 還使用了不同的記憶體分配器。

## <a name="pointer-support"></a><a name="_core_pointer_support"></a>指標支援

缺少調試資訊會從應用程式中刪除填充。 在發佈版本中,雜散指標更有可能指向未初始化的記憶體,而不是指向調試資訊。

## <a name="optimizations"></a><a name="_core_optimizations"></a>優化

根據某些代碼段的性質,優化編譯器可能會生成意外代碼。 這是發佈生成問題最不可能的原因,但確實偶爾會出現。 有關解決方案,請參閱[最佳資訊 。](optimizing-your-code.md)

## <a name="see-also"></a>另請參閱

[發行組建](release-builds.md)<br/>
[解決發行組建的問題](fixing-release-build-problems.md)
