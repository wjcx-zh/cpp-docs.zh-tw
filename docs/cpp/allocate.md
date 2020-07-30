---
title: allocate
ms.date: 11/04/2016
f1_keywords:
- allocate_cpp
helpviewer_keywords:
- __declspec keyword [C++], allocate
- allocate __declspec keyword
ms.assetid: 67828b31-de60-4c0e-b0a6-ef3aab22641d
ms.openlocfilehash: 0bf31423cd76c838cbeffa7458bbccb89592bf43
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227617"
---
# <a name="allocate"></a>allocate

**Microsoft 特定的**

宣告 **`allocate`** 規範會為將配置資料項目的資料區段命名。

## <a name="syntax"></a>語法

> **`__declspec(allocate("`***segname* **`))`***declarator*宣告子

## <a name="remarks"></a>備註

名稱*segname*必須使用下列其中一個 pragma 來宣告：

- [code_seg](../preprocessor/code-seg.md)

- [const_seg](../preprocessor/const-seg.md)

- [data_seg](../preprocessor/data-seg.md)

- [init_seg](../preprocessor/init-seg.md)

- [截面](../preprocessor/section.md)

## <a name="example"></a>範例

```cpp
// allocate.cpp
#pragma section("mycode", read)
__declspec(allocate("mycode"))  int i = 0;

int main() {
}
```

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[`__declspec`](../cpp/declspec.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
