---
title: 實值型別及其行為 (C + + /cli CLI) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- value types
ms.assetid: 5cb872a6-1e0a-429d-853d-df4ab47e8f2a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4d2d980e48a6f948c35faf0c4e42969795ef8dc7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404653"
---
# <a name="value-types-and-their-behaviors-ccli"></a>實值類型和行為 (C++/CLI)

實值型別變更以各種方式從 Managed Extensions for c + + 為 Visual c + +。 在本節中，我們看看 CLR 列舉型別和實值類別型別，以及查看 boxing 和 boxed 的執行個體，在 CLR 堆積中的存取權，以及了解內部和 pin 指標。 此區域中已有廣泛的語言變更。

## <a name="in-this-section"></a>本節內容

[CLR 列舉類型](../dotnet/value-types-and-their-behaviors-cpp-cli.md)<br/>
討論中的宣告和列舉行為的變更。

[實值型別的隱含 Boxing](../dotnet/implicit-boxing-of-value-types.md)<br/>
討論的動機隱含 boxing 實值型別和行為的後續變更。

[Boxed 值的追蹤控制代碼](../dotnet/a-tracking-handle-to-a-boxed-value.md)<br/>
討論如何隱含 boxing 值的型別會轉譯為 boxed 實的值物件的追蹤控制代碼。

[實值型別語意](../dotnet/value-type-semantics.md)<br/>
討論對實值類型語意，包括繼承虛擬方法、 類別預設建構函式、 內部指標和 pin 指標。

## <a name="see-also"></a>另請參閱

[C++/CLI 移轉入門](../dotnet/cpp-cli-migration-primer.md)<br/>
[類別和結構](../windows/classes-and-structs-cpp-component-extensions.md)