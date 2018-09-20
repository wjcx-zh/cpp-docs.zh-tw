---
title: 一般的語言變更 (C + + /cli CLI) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 79a70768-225c-4ae2-84d1-178b20a9b042
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9b48ebdf0bf25399b08f8a1cb1240a857cfad352
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418452"
---
# <a name="general-language-changes-ccli"></a>一般的語言變更 (C++/CLI)

從 Managed Extensions for c + + 變更為 Visual c + + 的 CLR 語言功能的數字。

在本節中所描述的變更是一種語言雜錄。 變更了字串常值中省略符號之間的多載解析的變更的處理和`Param`屬性，變更`typeof`到`typeid`，呼叫的建構函式初始設定式清單中的變更，引進新的轉換標記法的`safe_cast`。

[字串常值](../dotnet/string-literal.md)<br/>
討論如何變更字串常值的處理。

[Param 陣列和省略](../dotnet/param-array-and-ellipsis.md)<br/>
討論如何`ParamArray`現在提供優先的省略符號 (`...`) 來解析不同的數字的引數的函式呼叫。

[typeof 變成 T::typeid](../dotnet/typeof-goes-to-t-typeid.md)<br/>
討論如何`typeof`運算子已被取代的`typeid`。

[初始設定式清單](../dotnet/initializer-lists.md)<br/>
討論在初始設定式清單的呼叫順序中的變更。

[safe_cast<> 的轉換標記法和簡介](../dotnet/cast-notation-and-introduction-of-safe-cast-angles.md)<br/>
討論變更為轉換標記法，尤其是引進`safe_cast`。

## <a name="see-also"></a>另請參閱

[C++/CLI 移轉入門](../dotnet/cpp-cli-migration-primer.md)