---
title: 嚴重錯誤 C1060
ms.date: 11/04/2016
f1_keywords:
- C1060
helpviewer_keywords:
- C1060
ms.assetid: feaf305c-c84c-4160-b974-50e283412849
ms.openlocfilehash: f1a7c3ccab716a9281d4520f4c5fce2afff60187
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204434"
---
# <a name="fatal-error-c1060"></a>嚴重錯誤 C1060

編譯器堆積空間不足

作業系統或執行階段程式庫無法滿足記憶體要求。

### <a name="to-fix-this-error-try-the-following-possible-solutions"></a>若要修正這個錯誤，請嘗試下列可能的解決方案

1. 如果編譯器也發出錯誤[C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md)和[C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md)，請使用[/zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)編譯器選項來降低記憶體配置限制。 如果您降低剩餘的記憶體配置，應用程式將有更多堆積空間可用。

   如果已設定[/zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)選項，請嘗試將它移除。 堆積空間可能會因為選項中指定的記憶體配置上限太高而耗盡。 如果您移除[/zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)選項，編譯器會使用預設限制。

1. 如果您是在 64 位元平台上編譯，請使用 64 位元編譯器工具組。 如需相關資訊，請參閱[如何：在命令列上C++啟用64位的視覺化檢視](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)組。

1. 在32位 Windows 上，請嘗試使用[/3gb](https://support.microsoft.com/help/833721/available-switch-options-for-the-windows-xp-and-the-windows-server-200) boot.ini 參數。

1. 增加 Windows 交換檔的大小。

1. 關閉其他正在執行的程式。

1. 排除不必要的包含檔案。

1. 排除不必要的全域變數，例如動態地配置記憶體，而不宣告大型陣列。

1. 排除未使用到的宣告。

9. 將目前的檔案分割成較小的檔案。
