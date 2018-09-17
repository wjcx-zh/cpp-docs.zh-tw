---
title: -await （啟用協同程式支援） |Microsoft Docs
ms.custom: ''
ms.date: 08/15/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /await
- -await
dev_langs:
- C++
helpviewer_keywords:
- /await enable coroutine support [C++]
- -await enable coroutine support [C++]
- await enable coroutine support [C++]
ms.assetid: 302c8e69-09b6-4c58-bcdd-0a6a8713a8df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5da401f940a39c135ba0b64571b6330a42fed796
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725496"
---
# <a name="await-enable-coroutine-support"></a>/sdl （啟用協同程式支援）

使用 **/await**編譯器選項，啟用協同程式的編譯器支援。

## <a name="syntax"></a>語法

> / await

## <a name="remarks"></a>備註

**/Await**編譯器選項可讓編譯器支援 c + + 協同程式和關鍵字**co_await**， **co_yield**，和**co_return**. 根據預設，這個選項為關閉狀態。 在 Visual Studio 中的協同程式支援的相關資訊，請參閱[Visual Studio 小組部落格](https://blogs.msdn.microsoft.com/vcblog/category/coroutine/)。 如需詳細的協同程式的標準提案的詳細資訊，請參閱[N4628 Working Draft、 協同程式的 c + + 擴充功能的技術規格](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/n4628.pdf)。

**/Await**選項是在 Visual Studio 2015 開始提供。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟您的專案**屬性頁** 對話方塊。

2. 底下**組態屬性**，展開**C/c + +** 資料夾，然後選擇 **命令列**屬性頁。

3. 請輸入 **/await**中的編譯器選項**其他選項** 方塊中。 選擇 **[確定]** 或是**套用**以儲存變更。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)