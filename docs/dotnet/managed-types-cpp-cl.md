---
title: Managed 類型 (c + +-CL) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- __gc types
- types [C++], CLR
ms.assetid: 1ddd114e-be02-4de7-a4dd-a2d72ad8ff81
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 382228b9e8364d90d7929b4633744071c5eb0c77
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408026"
---
# <a name="managed-types-ccl"></a>Managed 類型 (C++/CL)

宣告 managed 型別，以及建立和使用這些類型的物件的語法已經大幅改變從 Managed Extensions for c + + Visual c + +。 這麼做是為了提升其 ISO c + + 型別系統中的整合。 這些變更會在下列小節中的詳細資料。

## <a name="in-this-section"></a>本節內容

[Managed 類別類型的宣告](../dotnet/declaration-of-a-managed-class-type.md)<br/>
討論如何宣告 managed `class`， `struct`，或`interface`。

[CLR 參考類別物件的宣告](../dotnet/declaration-of-a-clr-reference-class-object.md)<br/>
討論如何宣告使用的追蹤控制代碼的參考類別類型物件。

[CLR 陣列的宣告](../dotnet/declaration-of-a-clr-array.md)<br/>
說明如何宣告及初始化陣列。

[建構函式初始設定順序的變更](../dotnet/changes-in-constructor-initialization-order.md)<br/>
討論類別建構函式初始設定順序的主要變更。

[解構函式語意的變更](../dotnet/changes-in-destructor-semantics.md)<br/>
不具決定性的最終處理，將討論`Finalize`相對於`Dispose`，參考物件，與使用明確的後果`Finalize`。

**注意：** 委派的討論內容會延遲，直到[委派和事件](../dotnet/delegates-and-events.md)若要顯示在類別中，一般主題的事件成員[在類別或介面中的成員宣告(C + + /CLI CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md).

## <a name="see-also"></a>另請參閱

[C++/CLI 移轉入門](../dotnet/cpp-cli-migration-primer.md)<br/>
[類別和結構](../windows/classes-and-structs-cpp-component-extensions.md)<br/>
[陣列](../windows/arrays-cpp-component-extensions.md)