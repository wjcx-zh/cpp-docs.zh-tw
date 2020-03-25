---
title: 覆寫規範  (C++/CLI 和 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- override specifiers, C++
- override specifiers
ms.assetid: 155bbf6f-4722-4654-afb1-9cb52af799fb
ms.openlocfilehash: 410fe9ecc48b92c68132f7b1b8057c2549c8afcf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181898"
---
# <a name="override-specifiers--ccli-and-ccx"></a>覆寫規範  (C++/CLI 和 C++/CX)

「覆寫規範」會修改繼承型別和繼承型別的成員在衍生型別中的行為方式。

## <a name="all-runtimes"></a>所有執行階段

### <a name="remarks"></a>備註

如需覆寫規範的詳細資訊，請參閱：

- [abstract](abstract-cpp-component-extensions.md)

- [new (vtable 中的新位置)](new-new-slot-in-vtable-cpp-component-extensions.md)

- [override](override-cpp-component-extensions.md)

- [sealed](sealed-cpp-component-extensions.md)

- [覆寫規範和原生編譯](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)

**abstract** 和 **sealed** 也適用於型別宣告，而它們不會在其中做為覆寫規範。

如需明確覆寫基底類別函式的詳細資訊，請參閱[明確覆寫](explicit-overrides-cpp-component-extensions.md)。

## <a name="windows-runtime"></a>Windows 執行階段

(這個語言功能沒有只適用於 Windows 執行階段的備註。)

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

(這個語言功能沒有只適用於 Common Language Runtime 的備註。)

### <a name="requirements"></a>需求

編譯器選項：`/clr`

## <a name="see-also"></a>另請參閱

[適用於.NET 和 UWP 的元件延伸模組](component-extensions-for-runtime-platforms.md)
