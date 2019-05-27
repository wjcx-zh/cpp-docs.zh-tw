---
title: /CLRHEADER
ms.date: 05/16/2019
f1_keywords:
- /CLRHEADER
helpviewer_keywords:
- -CLRHEADER dumpbin option
- /CLRHEADER dumpbin option
- CLRHEADER dumpbin option
ms.assetid: cf73424f-4541-47e2-b94e-69b95266ef2a
ms.openlocfilehash: 5974606448dad103c8f12a126b8d17c688927c88
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837156"
---
# <a name="clrheader"></a>/CLRHEADER

顯示 CLR 特定資訊。

## <a name="syntax"></a>語法

> /CLRHEADER *file*

### <a name="arguments"></a>引數

*file*<br/>
使用 [/clr](clr-common-language-runtime-compilation.md) 建置的映像檔。

## <a name="remarks"></a>備註

**/CLRHEADER** 會顯示任何受控程式中使用的 .NET 標頭的相關資訊。 輸出會顯示 .NET 標頭以及標頭中各區段的位置和大小 (以位元組為單位)。

只有 [/HEADERS](headers.md) DUMPBIN 選項可用於以 [/GL](gl-whole-program-optimization.md) 編譯器選項產生的檔案上。

在以 /clr 編譯的檔案上使用 **/CLRHEADER** 時，dumpbin 輸出中會有 [CLR 標頭：] 區段。 **旗標**的值會指出已使用的 /clr 選項：

- 0  -- /clr (映像可能包含原生程式碼)。

您也可以用程式設計方式檢查是否已為通用語言執行平台建置映像。  如需詳細資訊，請參閱[如何：判斷映像為原生還是 CLR](../../dotnet/how-to-determine-if-an-image-is-native-or-clr.md)。

**/clr:pure** 和 **/clr:safe** 編譯器選項在 Visual Studio 2015 中已被取代，而且無法在 Visual Studio 2017 及更新版本中使用。 必須是「純」或「安全」程式碼才能移植到 C#。

## <a name="see-also"></a>另請參閱

- [DUMPBIN 選項](dumpbin-options.md)
