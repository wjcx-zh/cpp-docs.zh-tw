---
title: 發行的組建
ms.date: 11/04/2016
helpviewer_keywords:
- debugging [C++], release builds
- release builds
- debug builds, converting to release build
ms.assetid: fa9a78fa-f4b5-4722-baf4-aec655c4ff0f
ms.openlocfilehash: 77e02b424b10b5e9606cc49152c2e21d7eeed9cb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667450"
---
# <a name="release-builds"></a>發行的組建

發行組建會使用最佳化。 當您使用建立發行組建的最佳化時，則編譯器不會產生符號偵錯資訊。 呼叫的符號偵錯資訊的詳細資訊，以及追蹤和判斷提示不產生程式碼的事實不存在，表示可執行檔的大小會減少，並因此會更快。

此章節提供有關您為何和何時要將從偵錯組建中變更的發行組建。 它也會討論的一些變更從 「 偵錯發行組建時，可能會遇到的問題：

- [建立發行組建](../../build/reference/how-to-create-a-release-build.md)

- [建立發行組建時的常見問題](../../build/reference/common-problems-when-creating-a-release-build.md)

- [解決發行組建的問題](../../build/reference/fixing-release-build-problems.md)

   - [檢查 ASSERT 陳述式](../../build/reference/using-verify-instead-of-assert.md)

   - [使用偵錯組建檢查記憶體覆寫](../../build/reference/using-the-debug-build-to-check-for-memory-overwrite.md)

   - [偵錯發行組建](../../build/reference/how-to-debug-a-release-build.md)

   - [檢查記憶體覆寫](../../build/reference/checking-for-memory-overwrites.md)

## <a name="see-also"></a>另請參閱

[在 Visual Studio 中建置 C++ 專案](../../ide/building-cpp-projects-in-visual-studio.md)<br/>
[C/C++ 建置參考](../../build/reference/c-cpp-building-reference.md)