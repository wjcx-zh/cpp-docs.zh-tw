---
title: region、endregion pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.endregion
- endregion_CPP
- region_CPP
- vc-pragma.region
helpviewer_keywords:
- pragmas, region
- pragmas, endregion
- endregion pragma
- region pragma
ms.assetid: c697f807-622f-4796-851b-68a42bbecd84
ms.openlocfilehash: 4a01e04582ac81d678aa0702945c62ee974a4428
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222373"
---
# <a name="region-endregion-pragmas"></a>region、endregion pragma

`#pragma region`可讓您指定程式碼區塊, 當您使用 [Visual Studio Code 編輯器] 的[大綱功能](/visualstudio/ide/outlining)時, 可以展開或折迭它。

## <a name="syntax"></a>語法

> **#pragma 區域** *名稱*\
> **#pragma endregion** *批註*

### <a name="parameters"></a>參數

*加以*\
選擇性要顯示在程式碼編輯器中的批註。

*檔案名*\
選擇性區域的名稱。 這個名稱會顯示在程式碼編輯器中。

## <a name="remarks"></a>備註

`#pragma endregion`標記`#pragma region`區塊的結尾。

區塊必須以指示詞結束`#pragma endregion`。 `#region`

## <a name="example"></a>範例

```cpp
// pragma_directives_region.cpp
#pragma region Region_1
void Test() {}
void Test2() {}
void Test3() {}
#pragma endregion Region_1

int main() {}
```

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
