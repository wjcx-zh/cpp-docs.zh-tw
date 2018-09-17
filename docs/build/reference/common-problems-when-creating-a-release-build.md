---
title: 建立發行組建時的常見問題 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
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
- troubleshooting Visual C++
- troubleshooting release builds
- memory [C++], overwrites
ms.assetid: 73cbc1f9-3e33-472d-9880-39a8e9977b95
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b423f173bfa2d7fdc3fd8e97fe9eb42cf8e76f3d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702451"
---
# <a name="common-problems-when-creating-a-release-build"></a>建立發行組建時的常見問題

在開發期間，您通常會建置及測試與您專案的偵錯組建。 如果您再建置您的應用程式的發行組建，您可能會收到存取違規。

下列清單顯示偵錯和發行 （非偵錯） 組建的主要差異。 其他差異，但以下是當它是在偵錯組建中，會導致失敗的應用程式中的發行組建的主要差異。

- [堆積配置](#_core_heap_layout)

- [編譯](#_core_compilation)

- [指標的支援](#_core_pointer_support)

- [最佳化](#_core_optimizations)

請參閱[/GZ （攔截發行組建中的錯誤進行偵錯組建）](../../build/reference/gz-enable-stack-frame-run-time-error-checking.md)如需如何攔截版本的編譯器選項建置偵錯組建中的錯誤。

##  <a name="_core_heap_layout"></a> 堆積配置

堆積配置時，應用程式可以在偵錯，但未發行，將會約有 90%的明顯問題的原因。

當您建置您的專案進行偵錯時，您會使用偵錯記憶體配置器。 這表示所有記憶體配置都有其周圍放保護位元組。 這些保護位元組偵測記憶體覆寫。 因為不同之間發行和偵錯堆積配置記憶體覆寫的版本可能不會在偵錯組建中，建立的任何問題，但可能會造成嚴重的影響，在發行組建。

如需詳細資訊，請參閱 <<c0> [ 檢查記憶體覆寫](../../build/reference/checking-for-memory-overwrites.md)並[使用偵錯版檢查記憶體覆寫](../../build/reference/using-the-debug-build-to-check-for-memory-overwrite.md)。

##  <a name="_core_compilation"></a> 編譯

許多 MFC 巨集和大部分的 MFC 實作變更，當您建置發行版本。 特別的是，ASSERT 巨集判斷值為不在發行組建，因此會執行任何判斷提示中所找到的程式碼。 如需詳細資訊，請參閱 <<c0> [ 檢查 ASSERT 陳述式](../../build/reference/using-verify-instead-of-assert.md)。

有些函式是內嵌在發行組建中加快速度。 最佳化通常會在發行組建開啟。 也正在使用不同的記憶體配置器。

##  <a name="_core_pointer_support"></a> 指標的支援

偵錯資訊缺少會移除您的應用程式中的邊框距離。 在發行組建，偏離的指標會有比較有機會指向未初始化的記憶體，而不是指偵錯資訊。

##  <a name="_core_optimizations"></a> 最佳化

根據特定的程式碼區段的本質，最佳化編譯器可能會產生非預期的程式碼。 這是最不可能的原因的發行組建的問題，但在某些情況下，它會發生。 如需解決方案，請參閱[最佳化您的程式碼](../../build/reference/optimizing-your-code.md)。

## <a name="see-also"></a>另請參閱

[發行組建](../../build/reference/release-builds.md)<br/>
[解決發行組建的問題](../../build/reference/fixing-release-build-problems.md)