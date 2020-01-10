---
title: detect_mismatch pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.detect_mismatch
- detect_mismatch_CPP
helpviewer_keywords:
- pragmas, detect_mismatch
- detect_mismatch pragma
ms.assetid: ddb13ac9-0e2f-40ce-be69-7e44c04f5a12
ms.openlocfilehash: 6e247b3f251bce47710a3380fb295597314a3bd8
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222389"
---
# <a name="detect_mismatch-pragma"></a>detect_mismatch pragma

在物件中放入記錄。 連結器會檢查這些記錄是否有不相符之處。

## <a name="syntax"></a>語法

> **#pragma detect_mismatch (** "*name*" **,** "*value*" **)**

## <a name="remarks"></a>備註

當您連結專案時, 如果專案包含兩個具有相同*名稱*的物件, 但每個都有不同的*值*, 則連結器會擲回[LNK2038](../error-messages/tool-errors/linker-tools-error-lnk2038.md)錯誤。 使用這個 pragma 可防止連結不一致的目的檔。

[*名稱*] 和 [值] 都是字串常值, 而且會遵守關於 escape 字元和串連的字串常*值*規則。 它們會區分大小寫, 且不能包含逗號、等號、引號或**null**字元。

## <a name="example"></a>範例

這個範例會建立兩個版本號碼不同但版本標籤相同的檔案。

```cpp
// pragma_directive_detect_mismatch_a.cpp
#pragma detect_mismatch("myLib_version", "9")
int main ()
{
   return 0;
}

// pragma_directive_detect_mismatch_b.cpp
#pragma detect_mismatch("myLib_version", "1")
```

如果您使用命令列 `cl pragma_directive_detect_mismatch_a.cpp pragma_directive_detect_mismatch_b.cpp` 編譯這兩個檔案，將會收到 `LNK2038` 錯誤。

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
