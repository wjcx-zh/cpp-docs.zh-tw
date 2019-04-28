---
title: 連結器工具錯誤 LNK2033
ms.date: 11/04/2016
f1_keywords:
- LNK2033
helpviewer_keywords:
- LNK2033
ms.assetid: d61db467-9328-4788-bf54-e2a20537f13f
ms.openlocfilehash: 7e95823e23215848ff3e5d201171523c9009eb2d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298902"
---
# <a name="linker-tools-error-lnk2033"></a>連結器工具錯誤 LNK2033

'type' 的無法解析的 typeref 語彙基元 (token)

類型沒有定義 MSIL 中繼資料。

進行編譯時，可能會發生 LNK2033 **/clr: safe** ，並且可向前宣告型別的 MSIL 模組、 型別中的 MSIL 模組的參考位置。

型別必須定義下方 **/clr: safe**。

如需詳細資訊，請參閱 [/clr (Common Language Runtime 編譯)](../../build/reference/clr-common-language-runtime-compilation.md)。

## <a name="example"></a>範例

下列範例會產生 LNK2033。

```
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