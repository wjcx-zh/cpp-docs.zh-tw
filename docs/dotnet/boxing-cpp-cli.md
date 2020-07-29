---
title: Boxing (C++/CLI)
ms.date: 11/04/2016
ms.assetid: f4ee27a8-6a34-432d-b9ec-39285d513b23
ms.openlocfilehash: 03304b902ced2c1e9776eeec90142380b984ee45
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230905"
---
# <a name="boxing-ccli"></a>Boxing (C++/CLI)

「裝箱」是將實值型別轉換成型別或實值型別所實作為 `object` 任何介面型別的程式。 當 common language runtime （CLR）方塊為實值型別時，它會將值包裝在中， `System.Object` 並將它儲存在 managed 堆積上。 Unbox 處理則會從物件中擷取實值類型。 Boxing 是隱含處理，unboxing 則是明確處理。

## <a name="related-articles"></a>相關文章

|標題|說明|
|-----------|-----------------|
|[如何：明確要求裝箱](../dotnet/how-to-explicitly-request-boxing.md)|描述如何在變數上明確要求裝箱。|
|[如何：使用 gcnew 建立實數值型別及使用隱含的裝箱](../dotnet/how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing.md)|示範如何使用 **`gcnew`** 來建立可放在 managed 垃圾收集堆積上的已裝箱實數值型別。|
|[作法：Unbox](../dotnet/how-to-unbox.md)|顯示如何進行 Unbox 處理和修改值。|
|[標準轉換和隱含的裝箱](../dotnet/standard-conversions-and-implicit-boxing.md)|顯示編譯器在需要進行裝箱的轉換時選擇了標準轉換。|
|[使用 c + +/CLI 進行 .NET 程式設計（Visual C++）](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|在 Visual C++ 文件中關於 .NET 程式設計的最上層文件。|
