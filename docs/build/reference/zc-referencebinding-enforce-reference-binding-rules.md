---
title: /Zc:referenceBinding (強制執行參考繫結規則)
ms.date: 03/06/2018
f1_keywords:
- referenceBinding
- /Zc:referenceBinding
helpviewer_keywords:
- -Zc compiler options (C++)
- referenceBinding
- Enforce reference binding rules
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 0c6cfaac-9c2a-41a3-aa94-64ca8ef261fc
ms.openlocfilehash: b7e297d6fd913ddda4d44a42298a361e314af0b5
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518474"
---
# <a name="zcreferencebinding-enforce-reference-binding-rules"></a>/Zc:referenceBinding (強制執行參考繫結規則)

當您指定 **/zc： referenceBinding**選項時，編譯器不允許非 const 的左值參考系結至暫存。

## <a name="syntax"></a>語法

> **/Zc： referenceBinding**[ **-** ]

## <a name="remarks"></a>備註

如果已指定 **/zc： referenceBinding** ，則編譯器會遵循 c + + 11 標準的區段8.5.3：它不允許將使用者定義型別設為暫存的運算式系結至非 const 左值參考。 根據預設，或如果指定了 **/zc： referenceBinding-** ，編譯器會允許這類運算式做為 Microsoft 擴充功能，但會發出層級4警告。 針對程式碼安全性、可攜性和一致性，建議您使用 **/zc： referenceBinding**。

**/Zc： referenceBinding**選項預設為關閉。 [/Permissive-](permissive-standards-conformance.md)編譯器選項會隱含設定此選項，但可使用 **/zc： referenceBinding**來加以覆寫。

## <a name="example"></a>範例

這個範例會顯示 Microsoft 延伸模組，允許將使用者定義型別的暫存系結至非 const 左值參考。

```cpp
// zcreferencebinding.cpp
struct S {
};

void f(S&) {
}

S g() {
    return S{};
}

int main() {
    S& s = g();         // warning C4239 at /W4
    const S& cs = g();  // okay, bound to const ref
    f(g());             // Extension: error C2664 only if /Zc:referenceBinding
}
```

如需 Visual C++ 中一致性問題的詳細資訊，請參閱 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [組態屬性] > [C/C++] > [命令列] 屬性頁。

1. 修改 [**其他選項**] 屬性以包含 **/zc： referenceBinding** ，然後選擇 **[確定]** 。

## <a name="see-also"></a>請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
[/Zc (一致性)](zc-conformance.md)<br/>
