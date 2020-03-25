---
title: Boxing (C++/CLI)
ms.date: 11/04/2016
ms.assetid: f4ee27a8-6a34-432d-b9ec-39285d513b23
ms.openlocfilehash: df0e220c4f744e78aa5bedce4f956b726f524ff4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208825"
---
# <a name="boxing-ccli"></a>Boxing (C++/CLI)

「裝箱」是將實數值型別轉換為類型 `object` 或實數值型別所實作為任何介面類別型的程式。 當 common language runtime （CLR）方塊為實值型別時，它會將值包裝在 `System.Object` 中，並將它儲存在 managed 堆積上。 Unbox 處理則會從物件中擷取實值類型。 Boxing 是隱含處理，unboxing 則是明確處理。

## <a name="related-articles"></a>相關文章

|Title|描述|
|-----------|-----------------|
|[如何：明確要求 Boxing](../dotnet/how-to-explicitly-request-boxing.md)|描述如何在變數上明確要求裝箱。|
|[如何：使用 gcnew 建立實值型別及使用隱含 Boxing](../dotnet/how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing.md)|示範如何使用 `gcnew` 來建立可放在受管理之垃圾收集堆積上的已裝箱實數值型別。|
|[如何：Unbox](../dotnet/how-to-unbox.md)|顯示如何進行 Unbox 處理和修改值。|
|[標準轉換和隱含 Boxing](../dotnet/standard-conversions-and-implicit-boxing.md)|顯示編譯器在需要進行裝箱的轉換時選擇了標準轉換。|
|[以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|在 Visual C++ 文件中關於 .NET 程式設計的最上層文件。|
