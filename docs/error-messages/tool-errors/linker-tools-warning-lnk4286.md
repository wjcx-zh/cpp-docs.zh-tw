---
title: 連結器工具警告 LNK4286
ms.date: 04/15/2019
f1_keywords:
- LNK4286
helpviewer_keywords:
- LNK4286
ms.openlocfilehash: 43ed18808ba5ce632dd7dc7095f7bc30e4497ec9
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59674223"
---
# <a name="linker-tools-warning-lnk4286"></a>連結器工具警告 LNK4286

> 符號 '*符號*'中所定義的'*filename_1.obj*'匯入'*filename_2.obj*'

[__declspec （dllimport)](../../cpp/dllexport-dllimport.md)所指定*符號*即使在目的檔中已定義符號*filename_1.obj*相同的映像中。 移除`__declspec(dllimport)`修飾詞，以解決這個警告。

## <a name="remarks"></a>備註

警告 LNK4286 是更一般的版本[連結器工具警告 LNK4217](linker-tools-warning-lnk4217.md)。 它可以指出哪一個物件參考檔案的符號，但不是哪一個函式時，連結器就會產生警告 LNK4286。

若要解決 LNK4286，移除`__declspec(dllimport)`修飾詞宣告的向前宣告*符號*參考*filename_2.obj*。

雖然最終產生的程式碼會正確運作，來呼叫匯入的函式所產生的程式碼是效率比直接呼叫函式。 當您使用編譯時，不會出現這個警告[/clr](../../build/reference/clr-common-language-runtime-compilation.md)選項。

如需詳細資訊匯入和匯出資料宣告，請參閱 < [dllexport、 dllimport](../../cpp/dllexport-dllimport.md)。

## <a name="see-also"></a>另請參閱

[連結器工具警告 LNK4049](linker-tools-warning-lnk4049.md) \
[連結器工具警告 LNK4217](linker-tools-warning-lnk4217.md) \
[dllexport、dllimport](../../cpp/dllexport-dllimport.md)