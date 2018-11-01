---
title: 編譯器錯誤 C3850
ms.date: 09/05/2018
f1_keywords:
- C3850
helpviewer_keywords:
- C3850
ms.assetid: 028f3a37-f3ad-4ebc-9168-3cdea47524d4
ms.openlocfilehash: 9cd0428726f92c7347b162f74b46035f99cc2d3c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50572662"
---
# <a name="compiler-error-c3850"></a>編譯器錯誤 C3850

> '*char*': 通用字元名稱指定了無效的字元

## <a name="remarks"></a>備註

以通用字元名稱表示的字元必須代表 0-10FFFFF 範圍中的有效 Unicode 字碼指標。 通用字元名稱不能包含 Unicode Surrogate 範圍、D800 DFFF 或已編碼 Surrogate 字組中的值。 編譯器會自動從有效的字碼指標產生 Surrogate 字組。

在編譯為 C 程式碼，通用字元名稱不一定代表的字元範圍 0000 009F，內含與 0024 （' $'）、 0040 ('\@') 和 0060 (' ')。

在編譯為 C++ 的程式碼中，通用字元名稱可能會使用字串或字元常值中的任何有效 Unicode 字碼指標。 在常值以外，通用字元名稱不一定代表 0000-001F 或 007F-009F (含) 範圍中的控制字元，或基本來源字元集的成員。  如需詳細資訊，請參閱 [Character Sets](../../cpp/character-sets.md)。

## <a name="example"></a>範例

下列範例會產生 C3850，並示範如何修正此問題：

```cpp
// C3850.cpp
int main() {
   int \u0019 = 0;   // C3850, not in allowed range for an identifier
   const wchar_t * wstr_bad  = L"\UD840DC8A"; // C3850, UCN is surrogate pair
   const wchar_t * wstr_good = L"\U0002008A"; // Okay, UCN is valid code point
}
```