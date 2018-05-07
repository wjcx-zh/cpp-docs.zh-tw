---
title: 實值類型和它們的行為 (C + + /CLI) |Microsoft 文件
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
ms.openlocfilehash: 9c05d6198b57eeee473ab7a5ec467083a5783a55
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="value-types-and-their-behaviors-ccli"></a>實值類型和行為 (C++/CLI)
實值型別已變更以各種方式從 Managed Extensions for c + + Visual c + +。 在本節中，我們查看 CLR 列舉型別和值的類別類型，以及查看 boxing 和 boxed 到 CLR 堆積上，執行個體存取，以及查看內部和 pin 指標。 此區域中已有更詳盡的語言變更。  
  
## <a name="in-this-section"></a>本節內容  
 [CLR 列舉類型](../dotnet/value-types-and-their-behaviors-cpp-cli.md)  
 討論中的宣告和列舉的行為變更。  
  
 [實值型別的隱含 Boxing](../dotnet/implicit-boxing-of-value-types.md)  
 討論的動機隱含 boxing 實值類型和行為的後續變更。  
  
 [Boxed 值的追蹤控制代碼](../dotnet/a-tracking-handle-to-a-boxed-value.md)  
 討論如何隱含 boxing 值的型別會轉譯為 boxed 實的值物件的追蹤控制代碼。  
  
 [實值型別語意](../dotnet/value-type-semantics.md)  
 討論對實值類型語意，包括繼承的虛擬方法、 類別預設建構函式、 內部指標，pin 指標。  
  
## <a name="see-also"></a>另請參閱  
 [C + + /CLI 移轉入門](../dotnet/cpp-cli-migration-primer.md)   
 [類別和結構](../windows/classes-and-structs-cpp-component-extensions.md)