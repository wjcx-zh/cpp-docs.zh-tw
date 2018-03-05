---
title: "Boxing (C + + /CLI) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: f4ee27a8-6a34-432d-b9ec-39285d513b23
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e49c6f82099e6d7dbcfc47079d19228d7a91dc05
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="boxing-ccli"></a>Boxing (C++/CLI)
Boxing 是實值類型轉換成類型的程序`object`或實值型別所實作的任何介面類型。 當 common language runtime (CLR) box 實值類型時，它會將值包裝在`System.Object`並將它儲存在 managed 堆積上。 Unbox 處理則會從物件中擷取實值類型。 Boxing 是隱含處理，unboxing 則是明確處理。  
  
## <a name="related-articles"></a>相關文章  
  
|標題|描述|  
|-----------|-----------------|  
|[如何：明確要求 Boxing](../dotnet/how-to-explicitly-request-boxing.md)|描述如何明確要求 boxing 的變數上。|  
|[如何：使用 gcnew 建立實值型別及使用隱含 Boxing](../dotnet/how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing.md)|示範如何使用`gcnew`建立 boxed 實的值類型，可放置在受管理、 記憶體回收堆積上。|  
|[如何：Unbox](../dotnet/how-to-unbox.md)|顯示如何進行 Unbox 處理和修改值。|  
|[標準轉換和隱含 Boxing](../dotnet/standard-conversions-and-implicit-boxing.md)|顯示標準轉換選擇編譯器，需要進行 boxing 的轉換。|  
|[以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|在 Visual C++ 文件中關於 .NET 程式設計的最上層文件。|