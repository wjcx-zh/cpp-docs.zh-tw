---
title: /await (啟用協同程式支援)
ms.date: 08/15/2017
f1_keywords:
- /await
- -await
helpviewer_keywords:
- /await enable coroutine support [C++]
- -await enable coroutine support [C++]
- await enable coroutine support [C++]
ms.assetid: 302c8e69-09b6-4c58-bcdd-0a6a8713a8df
ms.openlocfilehash: eeab3f4a1afc73e341f04222a55c8ce429490742
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078440"
---
# <a name="await-enable-coroutine-support"></a>/await (啟用協同程式支援)

使用 **/await**編譯器選項來啟用協同程式的編譯器支援。

## <a name="syntax"></a>語法

> /await

## <a name="remarks"></a>備註

**/Await**編譯器C++選項會啟用協同程式的編譯器支援，以及**co_await**、 **co_yield**和**co_return**的關鍵字。 此選項預設是關閉。 如需 Visual Studio 中協同程式支援的相關資訊，請參閱[Visual Studio Team Blog](https://blogs.msdn.microsoft.com/vcblog/category/coroutine/)。 如需協同程式標準提案的詳細資訊，請參閱[N4628 工作草稿、適用于C++協同程式的延伸模組技術規格](https://wg21.link/n4628)。

**/Await**選項從 Visual Studio 2015 開始提供。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [**屬性頁**] 對話方塊。

1. 在 [設定**屬性**] 底下，展開 [ **CC++ /** ] 資料夾，然後選擇 [**命令列**] 屬性頁。

1. 在 [**其他選項**] 方塊中，輸入 **/await**編譯器選項。 選擇 **[確定]** **或 [** 套用] 以儲存變更。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>＞。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
