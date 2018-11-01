---
title: /CLRHEADER
ms.date: 11/04/2016
f1_keywords:
- /CLRHEADER
helpviewer_keywords:
- -CLRHEADER dumpbin option
- /CLRHEADER dumpbin option
- CLRHEADER dumpbin option
ms.assetid: cf73424f-4541-47e2-b94e-69b95266ef2a
ms.openlocfilehash: 864ecc0063716ce712e28b063714ce7c17fc294a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50627366"
---
# <a name="clrheader"></a>/CLRHEADER

顯示 CLR 特有的資訊。

## <a name="syntax"></a>語法

> /CLRHEADER*檔案*

### <a name="arguments"></a>引數

|||
|-|-|
*file*| 使用建置的映像檔[/clr](../../build/reference/clr-common-language-runtime-compilation.md)。

## <a name="remarks"></a>備註

**/CLRHEADER**顯示可用在任何受管理程式的.NET 標頭的相關資訊。 輸出會顯示的位置和大小，以位元組為單位，.NET 標頭以及標頭中的區段。

只有[/HEADERS](../../build/reference/headers.md) DUMPBIN 選項只適用於所產生的檔案上[/GL](../../build/reference/gl-whole-program-optimization.md)編譯器選項。

當 **/CLRHEADER**用在使用 /clr 所編譯的檔案上, 會有**clr 標頭：** dumpbin 輸出一節。 值**旗標**表示已使用哪些 /clr 選項：

- 0-/clr （映像可能會包含原生程式碼）。

您可以也以程式設計方式檢查是否專為通用語言執行平台映像的動作。  如需詳細資訊，請參閱 <<c0> [ 如何： 判斷影像是否為原生或 CLR](../../dotnet/how-to-determine-if-an-image-is-native-or-clr.md)。

**/Clr: pure**並 **/clr: safe**編譯器選項是在 Visual Studio 2015 中已被取代，而且不支援的 Visual Studio 2017 中。 必須是 「 純 」 或 「 安全 」 的程式碼才能移植到C#。

## <a name="see-also"></a>另請參閱

- [DUMPBIN 選項](../../build/reference/dumpbin-options.md)
