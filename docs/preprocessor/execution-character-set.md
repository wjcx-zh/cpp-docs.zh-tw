---
title: execution_character_set pragma
ms.date: 08/29/2019
f1_keywords:
- execution_character_set
- vc-pragma.execution_character_set
helpviewer_keywords:
- pragma execution_character_set
ms.assetid: 32248cbc-7c92-4dca-8442-230c052b53ad
ms.openlocfilehash: 0c2c812f27634f397af91eace7a41c0e71c1eb99
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218634"
---
# <a name="execution_character_set-pragma"></a>execution_character_set pragma

指定用於字串和字元常值的執行字元集。 標記`u8`為前置詞的常值不需要這個指示詞。

## <a name="syntax"></a>語法

> **#pragma execution_character_set (** "*target*" **)**

### <a name="parameters"></a>參數

*設定*\
指定目標執行字元集。 目前唯一支援的目標執行集為 "utf-8"。

## <a name="remarks"></a>備註

從 Visual Studio 2015 Update 2 開始, 這個編譯器指示詞已經過時。 我們建議您`/execution-charset:utf-8`將或`/utf-8`編譯器`u8`選項搭配使用, 並在包含擴充字元的窄字元和字串常值上使用前置詞。 如需`u8`前置詞的詳細資訊, 請參閱[字串和字元常](../cpp/string-and-character-literals-cpp.md)值。 如需編譯器選項的詳細資訊, 請參閱[/execution-charset (設定執行字元集)](../build/reference/execution-charset-set-execution-character-set.md)和[/Utf-8 (將來源和可執行檔字元集設定為 utf-8)](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)。

`#pragma execution_character_set("utf-8")`指示詞會告知編譯器將原始程式碼中的窄字元和窄字串常值編碼為可執行檔中的 utf-8。 此輸出編碼與所使用的來源檔案編碼無關。

根據預設, 編譯器會使用目前的字碼頁做為執行字元集, 將窄字元和窄字串編碼。 這表示在目前字碼頁範圍以外的常值中, Unicode 或 DBCS 字元會轉換成輸出中的預設取代字元。 Unicode 和 DBCS 字元會截斷為其低序位位元組。 這絕對不是您想要的。 您可以使用`u8`前置詞, 為原始程式檔中的常值指定 utf-8 編碼。 編譯器會將這些以 UTF-8 編碼的字串原封不動地傳遞至輸出。 前面加上 u8 的窄字元常值必須符合一個位元組, 否則會在輸出時被截斷。

根據預設, Visual Studio 會使用目前的字碼頁做為用來解讀原始程式碼以進行輸出的來源字元集。 當檔案已讀入時, 除非已設定檔案字碼頁, 或在檔案開頭偵測到位元組順序標記 (BOM) 或 UTF-16 字元, 否則 Visual Studio 會根據目前的字碼頁來加以解讀。 因為 UTF-8 無法設定為目前的字碼頁, 所以當自動偵測發現不含 BOM 的以 UTF-8 編碼的來源檔案時, Visual Studio 會假設它們是使用目前的字碼頁進行編碼。 原始程式檔中的字元若超出指定或自動偵測到的字碼頁範圍, 可能會導致編譯器警告和錯誤。

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和\_ \_pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[/execution-charset (設定執行字元集)](../build/reference/execution-charset-set-execution-character-set.md)\
[/utf-8 (將來源和可執行檔字元集設定為 UTF-8)](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)
