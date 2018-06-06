---
title: -CLRHEADER | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /CLRHEADER
dev_langs:
- C++
helpviewer_keywords:
- -CLRHEADER dumpbin option
- /CLRHEADER dumpbin option
- CLRHEADER dumpbin option
ms.assetid: cf73424f-4541-47e2-b94e-69b95266ef2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f6cda2f03e8a0473d2c45f54c96ca97b043d80d5
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704437"
---
# <a name="clrheader"></a>/CLRHEADER

顯示 CLR 特有的資訊。

## <a name="syntax"></a>語法

> /CLRHEADER*檔案*

### <a name="arguments"></a>引數

|||
|-|-|
*file*| 使用建立的映像檔[/clr](../../build/reference/clr-common-language-runtime-compilation.md)。

## <a name="remarks"></a>備註

**/CLRHEADER**顯示可用在任何受管理程式的.NET 標頭的相關資訊。 輸出會顯示的位置和大小，以位元組為單位的.NET 標頭和標頭中的章節。

只有[/HEADERS](../../build/reference/headers.md) DUMPBIN 選項僅適用於所產生的檔案上[/GL](../../build/reference/gl-whole-program-optimization.md)編譯器選項。

當 **/CLRHEADER**會使用以 /clr 編譯的檔案，會有**clr 標頭：** dumpbin 輸出中的區段。 值**旗標**表示已使用哪一個 /clr 選項：

- 0-/clr （映像可能包含原生程式碼）。

您也以程式設計方式可以檢查映像已針對 common language runtime。  如需詳細資訊，請參閱[How to： 判斷影像是否為原生或 CLR](../../dotnet/how-to-determine-if-an-image-is-native-or-clr.md)。

**/Clr: pure**和 **/clr: safe**編譯器選項都是 Visual Studio 2015 中已被取代，並不支援的 Visual Studio 2017 中。 必須是 「 單純的 」 或 「 安全 」 的程式碼應該移植到 C#。

## <a name="see-also"></a>另請參閱

- [DUMPBIN 選項](../../build/reference/dumpbin-options.md)
