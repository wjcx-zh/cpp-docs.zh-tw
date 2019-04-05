---
title: region、endregion
ms.date: 10/18/2018
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
ms.openlocfilehash: c73a90aa2be83d643b74dde4645081e89da3ff73
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037922"
---
# <a name="region-endregion"></a>region、endregion

`#pragma region` 可讓您指定的程式碼，您可以展開或摺疊時使用的區塊[大綱功能](/visualstudio/ide/outlining)的 Visual Studio 程式碼編輯器。

## <a name="syntax"></a>語法

```
#pragma region name
#pragma endregion comment
```

### <a name="parameters"></a>參數

*註解*<br/>
（選擇性）將會顯示在程式碼編輯器中的註解。

*名稱*<br/>
（選擇性）區域的名稱。  此名稱會顯示在程式碼編輯器中。

## <a name="remarks"></a>備註

`#pragma endregion` 標記的結尾`#pragma region`區塊。

A`#region`區塊必須以結束`#pragma endregion`。

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

[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)