---
title: /GT (支援 Fiber-Safe 執行緒區域儲存區)
ms.date: 11/04/2016
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
ms.openlocfilehash: 417ac00a446f773a424553e42478a4f0cf58efc6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291804"
---
# <a name="gt-support-fiber-safe-thread-local-storage"></a>/GT (支援 Fiber-Safe 執行緒區域儲存區)

使用靜態執行緒區域儲存區，也就是以所配置的資料配置的資料支援 fiber 安全性`__declspec(thread)`。

## <a name="syntax"></a>語法

```
/GT
```

## <a name="remarks"></a>備註

使用宣告資料`__declspec(thread)`參考透過執行緒區域儲存區 (TLS) 陣列。 TLS 陣列是的系統會維護每個執行緒的位址陣列。 此陣列中的每個位址可讓執行緒區域儲存區資料的位置。

Fiber 是輕量型的物件，包含堆疊和暫存器內容，並可在各種不同的執行緒上排程。 Fiber 可以在任何執行緒上執行。 由於 fiber 可能取得交換，而且稍後重新啟動不同的執行緒，TLS 陣列的位址必須不是快取或最佳化的通用子運算式為跨函式呼叫 (請參閱[/Og （全域最佳化）](og-global-optimizations.md)選項詳細資料）。 **/GT**可避免這種最佳化。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)。</c0>

1. 按一下 [C/C++]  資料夾。

1. 按一下 **最佳化**屬性頁。

1. 修改**啟用 fiber-safe 最佳化**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFiberSafeOptimizations%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
