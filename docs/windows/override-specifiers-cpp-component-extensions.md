---
title: 覆寫規範 (C + + /cli 和 C + + /CX) |Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- override specifiers, C++
- override specifiers
ms.assetid: 155bbf6f-4722-4654-afb1-9cb52af799fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0620bc7045dcb312667cfdfe670e1f19b0545cf2
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2018
ms.locfileid: "49327460"
---
# <a name="override-specifiers--ccli-and-ccx"></a>覆寫規範 (C + + /cli 和 C + + /CX)

*覆寫規範*修改如何繼承的型別和繼承型別成員的衍生型別中的行為。

## <a name="all-runtimes"></a>所有執行階段

### <a name="remarks"></a>備註

如需覆寫規範的詳細資訊，請參閱：

- [abstract](../windows/abstract-cpp-component-extensions.md)

- [new （新位置 vtable 中）](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)

- [override](../windows/override-cpp-component-extensions.md)

- [sealed](../windows/sealed-cpp-component-extensions.md)

- [覆寫規範和原生編譯](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)

**抽象**並**密封**也是有效的型別宣告，其中它們不會套用為覆寫規範。

如需明確覆寫基底類別函式的資訊，請參閱 <<c0> [ 明確覆寫](../windows/explicit-overrides-cpp-component-extensions.md)。

## <a name="windows-runtime"></a>Windows 執行階段

(這個語言功能沒有只適用於 Windows 執行階段的備註。)

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

(這個語言功能沒有只適用於 Common Language Runtime 的備註。)

### <a name="requirements"></a>需求

編譯器選項：`/clr`

## <a name="see-also"></a>另請參閱

[適用於.NET 和 UWP 的元件擴充功能](../windows/component-extensions-for-runtime-platforms.md)