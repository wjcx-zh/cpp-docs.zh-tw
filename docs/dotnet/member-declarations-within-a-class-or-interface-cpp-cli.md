---
title: 在類別或介面中的成員宣告 (C + + /cli CLI) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- members, declaration syntax
- class members, declaration syntax
ms.assetid: 95d312a4-198b-46f0-b8f5-15253807c55e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 80b872b4c614677c05b0d28b821d3a48255905c5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430629"
---
# <a name="member-declarations-within-a-class-or-interface-ccli"></a>在類別或介面中的成員宣告 (C++/CLI)

屬性和運算子的宣告具有已廣泛重新撰寫，從 Managed Extensions for c + + Visual c + +，隱藏已公開 Managed Extensions 設計中的基礎實作詳細資料。 也已修改事件宣告。

類別的變更有任何 Managed Extensions 的支援，現在在靜態建構函式可以是定義的外行 （它們必須是 Managed Extensions 中的內嵌定義），以及委派的建構函式的概念也推出了。

## <a name="in-this-section"></a>本節內容

[屬性宣告](../dotnet/property-declaration.md)<br/>
討論屬性宣告的變更。

[屬性索引宣告](../dotnet/property-index-declaration.md)<br/>
討論變更索引的屬性宣告。

[委派和事件](../dotnet/delegates-and-events.md)<br/>
討論用來宣告委派和事件的語法變更。

[密封虛擬函式](../dotnet/sealing-a-virtual-function.md)<br/>
討論變更密封函式的語法。

[多載運算子](../dotnet/overloaded-operators.md)<br/>
討論多載的運算子的變更。

[轉換運算子的變更](../dotnet/changes-to-conversion-operators.md)<br/>
討論轉換運算子的變更。

[介面成員的明確覆寫](../dotnet/explicit-override-of-an-interface-member.md)<br/>
討論的方法明確覆寫介面成員的變更。

[私用虛擬函式](../dotnet/private-virtual-functions.md)<br/>
討論在私用虛擬函式在衍生類別中處理的方式中的變更。

[靜態 Const 整數連結不再是常值](../dotnet/static-const-int-linkage-is-no-longer-literal.md)<br/>
討論的方式變更`static const`連結整數類資料的成員，以及如何明確地宣告使用新的常數`literal`關鍵字。

## <a name="see-also"></a>另請參閱

[C++/CLI 移轉入門](../dotnet/cpp-cli-migration-primer.md)