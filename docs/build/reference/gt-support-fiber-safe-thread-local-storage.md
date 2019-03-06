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
ms.openlocfilehash: 14d2f66401b7b7ed324b79b12b6de26c7ee450b2
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57420254"
---
# <a name="gt-support-fiber-safe-thread-local-storage"></a>/GT (支援 Fiber-Safe 執行緒區域儲存區)

使用靜態執行緒區域儲存區，也就是以所配置的資料配置的資料支援 fiber 安全性`__declspec(thread)`。

## <a name="syntax"></a>語法

```
/GT
```

## <a name="remarks"></a>備註

使用宣告資料`__declspec(thread)`參考透過執行緒區域儲存區 (TLS) 陣列。 TLS 陣列是的系統會維護每個執行緒的位址陣列。 此陣列中的每個位址可讓執行緒區域儲存區資料的位置。

Fiber 是輕量型的物件，包含堆疊和暫存器內容，並可在各種不同的執行緒上排程。 Fiber 可以在任何執行緒上執行。 由於 fiber 可能取得交換，而且稍後重新啟動不同的執行緒，TLS 陣列的位址必須不是快取或最佳化的通用子運算式為跨函式呼叫 (請參閱[/Og （全域最佳化）](../../build/reference/og-global-optimizations.md)選項詳細資料）。 **/GT**可避免這種最佳化。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 [C/C++]  資料夾。

1. 按一下 **最佳化**屬性頁。

1. 修改**啟用 fiber-safe 最佳化**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFiberSafeOptimizations%2A>。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)
