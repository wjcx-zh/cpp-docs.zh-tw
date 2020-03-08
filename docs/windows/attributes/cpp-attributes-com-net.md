---
title: 適用於 COM 和 .NET 的 C++ 屬性
ms.custom: index-page
ms.date: 11/19/2018
ms.topic: conceptual
helpviewer_keywords:
- attributes [C++/CLI], reference topics
ms.assetid: 613a3611-b3eb-4347-aa38-99b654600e1c
ms.openlocfilehash: 4885edf57988d5f83b56ba6a71da85877354d3ce
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856438"
---
# <a name="c-attributes-for-com-and-net"></a>適用於 COM 和 .NET 的 C++ 屬性

Microsoft 會定義一組C++屬性，以簡化 COM 程式設計和 .NET Framework common language runtime 開發。 當您在來源檔案中包含屬性時，編譯器會與提供者 Dll 搭配使用，以插入程式碼或修改所產生之物件檔案中的程式碼。 這些屬性有助於建立 .idl 檔案、介面、型別程式庫和其他 COM 元素。 在整合式開發環境（IDE）中，屬性是由 [程式] 和 [屬性視窗] 所支援。

雖然屬性可以排除撰寫 COM 物件所需的一些詳細程式碼，但您需要[COM 基本](/windows/win32/com/the-component-object-model)概念的背景，才能發揮最大用途。

> [!NOTE]
> 如果您要尋找C++標準屬性，請參閱[屬性](../../cpp/attributes.md)。

## <a name="purpose-of-attributes"></a>屬性用途

屬性目前C++不可能延伸，而不會破壞語言的傳統結構。 屬性可讓提供者（個別的 Dll）動態擴充語言功能。 屬性的主要目標是要簡化 COM 元件的撰寫，以及增加元件開發人員的生產力層級。 屬性可以套用至幾乎任何C++結構，例如類別、資料成員或成員函式。 以下是這項新技術所提供的優勢重點：

- 公開熟悉且簡單的呼叫慣例。

- 使用與宏不同的插入程式碼，可由偵錯工具辨識。

- 可輕鬆地從基類衍生，而不需要繁瑣的執行詳細資料。

- 以一些精簡的屬性取代 COM 元件所需的大量 IDL 程式碼。

例如，若要為泛型 ATL 類別執行簡單的事件接收，您可以將[event_receiver](event-receiver.md)屬性套用至特定類別，例如 `CMyReceiver`。 然後，Microsoft C++編譯器會編譯 `event_receiver` 屬性，這會將適當的程式碼插入至物件檔案。

```cpp
[event_receiver(com)]
class CMyReceiver
{
   void handler1(int i) { ... }
   void handler2(int i, float j) { ... }
}
```

接著，您可以設定 `CMyReceiver` 方法 `handler1` 和 `handler2` 來處理事件來源的事件（使用內建函式[__hook](../../cpp/hook.md)），您可以使用[event_source](event-source.md)來建立該事件。

## <a name="basic-mechanics-of-attributes"></a>屬性的基本機制

有三種方式可將屬性插入您的專案中。 首先，您可以手動將它們插入原始程式碼中。 第二，您可以使用專案中物件的屬性方格來插入它們。 最後，您可以使用各種不同的嚮導來插入它們。 如需有關使用 [**屬性**] 視窗和各種不同的程式的詳細資訊，請參閱[Visual Studio 專案- C++ ](../../build/creating-and-managing-visual-cpp-projects.md)。

如先前所述，建立專案時，編譯器會剖析每C++個來源檔案，並產生一個物件檔案。 不過，當編譯器遇到屬性時，會進行剖析並進行語法驗證。 然後編譯器會動態地呼叫屬性提供者來插入程式碼，或在編譯時期進行其他修改。 提供者的執行會因屬性的類型而有所不同。 例如，與 ATL 相關的屬性是由 Atlprov 所執行。

下圖將示範編譯器和屬性提供者之間的關聯性。

![元件屬性通訊](../media/vccompattrcomm.gif "元件屬性通訊")

> [!NOTE]
> 屬性使用方式不會改變來源檔案的內容。 只有在偵測會話期間，才會顯示產生的屬性程式碼。 此外，針對專案中的每個原始程式檔，您可以產生文字檔，以顯示內容替代的結果。 如需此程式的詳細資訊，請參閱[/fx （合併插入的程式碼）](../../build/reference/fx-merge-injected-code.md)和[偵錯工具插入程式碼](/visualstudio/debugger/how-to-debug-injected-code)。

如同大部分C++的結構，屬性具有一組特性，可定義其適當的使用方式。 這稱為屬性的內容，並在每個屬性參考主題的屬性內容資料表中加以處理。 例如， [coclass](coclass.md)屬性只能套用至現有的類別或結構，而不是[cpp_quote](cpp-quote.md)屬性，可以插入C++原始程式檔內的任何位置。

## <a name="building-an-attributed-program"></a>建置屬性化程式

在您將視覺C++屬性放入原始程式碼之後，您可能會想要C++ Microsoft 編譯器為您產生型別程式庫和 .idl 檔案。 下列連結器選項可協助您建立 .tlb 和 .idl 檔案：

- [/IDLOUT](../../build/reference/idlout-name-midl-output-files.md)

- [/IGNOREIDL](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)

- [/MIDL](../../build/reference/midl-specify-midl-command-line-options.md)

- [/TLBOUT](../../build/reference/tlbout-name-dot-tlb-file.md)

某些專案包含多個獨立的 .idl 檔案。 這些是用來產生兩個或多個 .tlb 檔案，並選擇性地將它們系結至資源區塊。 視覺效果C++目前不支援此案例。

此外，視覺C++連結器會將所有 IDL 相關的屬性資訊輸出至單一 MIDL 檔案。 將無法從單一專案產生兩個類型程式庫。

## <a name="contexts"></a>屬性內容

C++屬性可以使用四個基本欄位來描述：可以套用至的目標（**適用**于），如果它們可重複或不是（可**重複**）、需要的其他屬性（**必要的屬性**）存在，以及與其他屬性不相容（不正確**屬性**）。 這些欄位會列在每個屬性參考主題的隨附資料表中。 以下說明每一個欄位。

### <a name="applies-to"></a>套用至

此欄位描述屬於指定C++屬性之合法目標的不同語言元素。 例如，如果屬性在 [**適用**于] 欄位中指定 "class"，這表示該屬性只能套用至合法C++類別。 如果將屬性套用至類別的成員函式，則會產生語法錯誤。

如需詳細資訊，請參閱[依使用量的屬性](attributes-by-usage.md)。

### <a name="repeatable"></a>可重複

此欄位說明屬性是否可以重複套用至相同的目標。 大部分的屬性都不是可重複的。

### <a name="required-attributes"></a>需要的屬性

這個欄位會列出必須存在的其他屬性（也就是套用到相同的目標），指定的屬性才能正常運作。 屬性對於此欄位有任何專案是很罕見的。

### <a name="invalid-attributes"></a>不正確屬性

此欄位會列出與指定屬性不相容的其他屬性。 屬性對於此欄位有任何專案是很罕見的。

## <a name="in-this-section"></a>本節內容

[屬性程式設計常見問題集](attribute-programming-faq.md)<br/>
[依群組分類的屬性](attributes-by-group.md)<br/>
[依使用方式分類的屬性](attributes-by-usage.md)<br/>
[依字母順序排列的屬性參考](attributes-alphabetical-reference.md)