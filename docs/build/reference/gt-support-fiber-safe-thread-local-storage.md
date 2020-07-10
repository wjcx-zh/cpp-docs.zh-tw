---
title: /GT (支援 Fiber-Safe 執行緒本機存放區)
description: MSVC 編譯器選項/GT 會啟用執行緒區域儲存資料的安全優化。
ms.date: 07/08/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableFiberSafeOptimizations
- /gt
helpviewer_keywords:
- /GT compiler option [C++]
- GT compiler option [C++]
- thread-local storage
- static thread-local storage and fiber safety
- -GT compiler option [C++]
- fiber-safe static thread-local storage compiler option [C++]
ms.assetid: 071fec79-c701-432b-9970-457344133159
ms.openlocfilehash: 1b1d9f6514cec8c3d247f86be063f2ac3e0dfe72
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180808"
---
# <a name="gt-support-fiber-safe-thread-local-storage"></a>`/GT` (支援以光纖安全的執行緒本機儲存) 

針對使用靜態執行緒區域儲存區（也就是使用所配置的資料）所配置的資料，支援光纖安全 `__declspec(thread)` 。

## <a name="syntax"></a>語法

> **`/GT`**

## <a name="remarks"></a>備註

使用宣告的資料 `__declspec(thread)` 會透過執行緒區域儲存區（ (TLS) 陣列）來參考。 TLS 陣列是系統為每個執行緒維護的位址陣列。 此陣列中的每個位址都會提供執行緒區域儲存資料的位置。

「光纖」是輕量物件，其中包含堆疊和暫存器內容，而且可以在各種執行緒上排程。 光纖可以在任何執行緒上執行。 因為光纖可能會在稍後的不同執行緒上交換並重新啟動，所以編譯器不得會快取 TLS 陣列的位址，或將它優化為跨函式呼叫的通用子運算式。 **`/GT`** 防止這類優化。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**] [  >  **c/c + +**  >  **優化**] 屬性頁。

1. 修改 [**啟用光纖安全優化**] 屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜ <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFiberSafeOptimizations%2A> ＞。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
