---
title: 連結器工具錯誤 LNK2033
ms.date: 11/04/2016
f1_keywords:
- LNK2033
helpviewer_keywords:
- LNK2033
ms.assetid: d61db467-9328-4788-bf54-e2a20537f13f
ms.openlocfilehash: 407f5eaf94a0e2da43425c3bbdd1955a88c95f14
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991185"
---
# <a name="linker-tools-error-lnk2033"></a>連結器工具錯誤 LNK2033

' type ' 的無法解析的 typeref 標記（token）

類型在 MSIL 中繼資料中沒有定義。

以 **/clr： safe**進行編譯時，如果 msil 模組中的型別只有一個向前宣告，在 msil 模組中參考型別，則可能會發生 LNK2033。

類型必須在 **/clr： safe**之下定義。

如需詳細資訊，請參閱 [/clr (Common Language Runtime 編譯)](../../build/reference/clr-common-language-runtime-compilation.md)。

## <a name="example"></a>範例

下列範例會產生 LNK2033。

```cpp
// LNK2033.cpp
// compile with: /clr:safe
// LNK2033 expected
ref class A;
ref class B {};

int main() {
   A ^ aa = nullptr;
   B ^ bb = nullptr;   // OK
};
```
