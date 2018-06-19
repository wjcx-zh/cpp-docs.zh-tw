---
title: Managed 類型 (c + + CL) |Microsoft 文件
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
ms.openlocfilehash: 42426c45f4b8caf3cd4cb61ee867470dc9ea639f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33135855"
---
# <a name="managed-types-ccl"></a>Managed 類型 (C++/CL)
針對 managed 型別和建立的宣告和使用這些型別的物件語法已經大幅改變，從 Managed Extensions for c + + Visual c + +。 這是要提升其 ISO c + + 類型系統中的整合。 這些變更會以下列小節將詳細說明。  
  
## <a name="in-this-section"></a>本節內容  
 [Managed 類別類型的宣告](../dotnet/declaration-of-a-managed-class-type.md)  
 討論如何宣告 managed `class`， `struct`，或`interface`。  
  
 [CLR 參考類別物件的宣告](../dotnet/declaration-of-a-clr-reference-class-object.md)  
 討論如何使用追蹤控制代碼的參考類別類型物件的宣告。  
  
 [CLR 陣列的宣告](../dotnet/declaration-of-a-clr-array.md)  
 說明如何宣告和初始化陣列。  
  
 [建構函式初始設定順序的變更](../dotnet/changes-in-constructor-initialization-order.md)  
 討論在類別建構函式初始化順序中的金鑰變更。  
  
 [解構函式語意的變更](../dotnet/changes-in-destructor-semantics.md)  
 討論不具決定性最終處理，`Finalize`與`Dispose`，針對參考的物件和使用明確的細節`Finalize`。  
  
 **注意：** 委派的討論內容會延遲，直到[委派和事件](../dotnet/delegates-and-events.md)呈現其事件類別時，一般的主題內的成員具有[類別或介面中的成員宣告(C + + /CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md).  
  
## <a name="see-also"></a>另請參閱  
 [C + + /CLI 移轉入門](../dotnet/cpp-cli-migration-primer.md)   
 [類別和結構](../windows/classes-and-structs-cpp-component-extensions.md)   
 [陣列](../windows/arrays-cpp-component-extensions.md)