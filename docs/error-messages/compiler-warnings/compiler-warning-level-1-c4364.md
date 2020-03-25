---
title: 編譯器警告 (層級 1) C4364
ms.date: 11/04/2016
f1_keywords:
- C4364
helpviewer_keywords:
- C4364
ms.assetid: 1477634c-d60f-4570-ad16-1aaeae24ac7f
ms.openlocfilehash: 79c8809b4de9d6853aaacec4283bf01d0e89305e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187098"
---
# <a name="compiler-warning-level-1-c4364"></a>編譯器警告 (層級 1) C4364

\#針對先前在位置（line_number）所看到的元件 ' file ' 使用，而不 as_friend 屬性;as_friend 不適用

指定的中繼資料檔案已重複 `#using` 指示詞，但在第一次出現時未使用 `as_friend` 限定詞;編譯器會忽略第二個 `as_friend`。

如需詳細資訊，請參閱[FriendC++元件（）](../../dotnet/friend-assemblies-cpp.md)。

## <a name="example"></a>範例

下列範例會建立元件。

```cpp
// C4364.cpp
// compile with: /clr /LD
ref class A {};
```

## <a name="example"></a>範例

下列範例會產生 C4364。

```cpp
// C4364_b.cpp
// compile with: /clr /W1 /c
#using " C4364.dll"
#using " C4364.dll" as_friend   // C4364
```
