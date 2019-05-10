---
title: C++適用於 COM 和.NET 屬性
ms.custom: index-page
ms.date: 11/19/2018
ms.topic: conceptual
helpviewer_keywords:
- attributes [C++/CLI], reference topics
ms.assetid: 613a3611-b3eb-4347-aa38-99b654600e1c
ms.openlocfilehash: 9b985799849a268010dff63f9f7bc25e474b365e
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2019
ms.locfileid: "65448509"
---
# <a name="c-attributes-for-com-and-net"></a>C++適用於 COM 和.NET 屬性

Microsoft 定義一組C++屬性可簡化 COM 程式設計與.NET Framework 通用語言執行階段開發。 當您將屬性納入原始程式檔時，編譯器會搭配提供者來插入程式碼，或修改產生的物件檔案的程式碼的 Dll。 這些屬性可協助建立.idl 檔案、 介面、 型別程式庫，以及其他 COM 元件。 在整合式的開發環境 (IDE) 中，由精靈和 [屬性] 視窗所支援屬性。

雖然屬性排除某些撰寫 COM 物件所需的詳細編碼，您需要在背景[COM fundamentals](/windows/desktop/com/the-component-object-model)最適合使用它們。

> [!NOTE]
> 如果您要尋找的C++標準屬性，請參閱[屬性](../../cpp/attributes.md)。

## <a name="purpose-of-attributes"></a>屬性用途

擴充屬性C++目前無法而不會中斷語言的傳統結構的方向。 屬性可讓提供者 (另一個 Dll) 來動態擴充的語言功能。 屬性的主要目標是簡化 COM 元件，以及增加元件開發人員的產能層級的撰寫。 屬性可以套用到幾乎任何C++建構，例如類別、 資料成員或成員函式。 以下是提供這項新技術的優勢的反白顯示：

- 會公開熟悉且簡單的呼叫慣例。

- 使用插入程式碼，這不同於巨集，辨識偵錯工具。

- 可讓您輕鬆衍生自基底類別，而不麻煩的實作詳細資料。

- 取代了大量的所需的幾個簡要的屬性與 COM 元件的 IDL 程式碼。

例如，若要實作一般的 ATL 類別的簡單事件接收器，您可以套用[event_receiver](event-receiver.md)屬性，是特定的類別例如`CMyReceiver`。 `event_receiver`屬性就會編譯由 MicrosoftC++編譯器，並將適當的程式碼插入物件檔案。

```cpp
[event_receiver(com)]
class CMyReceiver
{
   void handler1(int i) { ... }
   void handler2(int i, float j) { ... }
}
```

您接著可以設定`CMyReceiver`方法`handler1`並`handler2`來處理事件 (使用內建函式[__hook](../../cpp/hook.md)) 從事件來源，您可以建立使用[event_source](event-source.md).

## <a name="basic-mechanics-of-attributes"></a>屬性的基本機制

有三種方式，將屬性插入您的專案。 首先，您可以將它們插入以手動方式插入原始程式碼中。 第二，您可以將它們插入在專案中使用物件的屬性方格。 最後，您可以將它們插入使用各種不同的精靈。 如需有關使用**屬性** 視窗和各種精靈，請參閱[Visual Studio 專案- C++ ](../../build/creating-and-managing-visual-cpp-projects.md)。

如往常一般，當建置專案時，編譯器會剖析每個C++原始程式檔，產生的物件檔案。 不過，當編譯器發現屬性，它會剖析並語法驗證。 然後編譯器動態地呼叫插入程式碼，或在編譯時期進行其他修改的屬性提供者。 提供者的實作是根據屬性的類型而有所不同。 比方說，ATL 相關屬性的實作方式 Atlprov.dll。

下圖示範編譯器和屬性提供者之間的關聯性。

![元件屬性通訊](../media/vccompattrcomm.gif "元件屬性通訊")

> [!NOTE]
> 屬性使用方式不會更改原始程式檔的內容。 產生的屬性程式碼會顯示的唯一時間是在偵錯工作階段期間。 此外，在專案中每個原始程式檔，您可以產生文字檔案，以顯示屬性的替代結果。 如需有關此程序的詳細資訊，請參閱 < [/Fx （合併插入程式碼）](../../build/reference/fx-merge-injected-code.md)並[偵錯插入程式碼](/visualstudio/debugger/how-to-debug-injected-code)。

例如大部分C++建構，屬性具有一組特性，定義其適當的使用方式。 這指做為屬性的內容，並在屬性內容表的每一個屬性參考主題中已解決。 例如， [coclass](coclass.md)屬性可以只套用至現有的類別或結構，而不是[cpp_quote](cpp-quote.md)屬性，可在任何位置插入C++原始程式檔。

## <a name="building-an-attributed-program"></a>建置屬性化程式

您將視覺效果之後C++屬性到您的原始程式碼，您可能想 MicrosoftC++編譯器為您產生類型程式庫和.idl 檔案。 下列連結器選項建置.tlb 和.idl 檔案的說明：

- [/IDLOUT](../../build/reference/idlout-name-midl-output-files.md)

- [/IGNOREIDL](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)

- [/MIDL](../../build/reference/midl-specify-midl-command-line-options.md)

- [/TLBOUT](../../build/reference/tlbout-name-dot-tlb-file.md)

有些專案包含多個獨立的.idl 檔案。 這些用來產生兩個以上的.tlb 檔案，並選擇性地將其繫結至資源區塊。 此案例中目前不支援在視覺效果C++。

此外，視覺效果C++連結器將會輸出單一 MIDL 檔的所有相關的 IDL 屬性資訊。 會沒有辦法從單一專案中產生兩個型別程式庫。

## <a name="contexts"></a> 屬性內容

C++屬性可以使用四個基本的欄位描述： 它們可以套用到目標 (**適用對象**)，如果它們是可重複，或是不 (**Repeatable**)、 所需的其他屬性的目前狀態 (**所需屬性**)，並與其他屬性的不相容 (**無效的屬性**)。 隨附的資料表中每個屬性的參考主題會列出這些欄位。 以下說明每個欄位。

### <a name="applies-to"></a>適用於

此欄位描述不同C++是指定之屬性的合法目標的語言項目。 比方說，如果屬性會指定 「 類別 」 中**適用對象**欄位，這會指示屬性只套用至為合法C++類別。 如果屬性套用至類別的成員函式，會產生語法錯誤。

如需詳細資訊，請參閱 <<c0> [ 屬性的用法](attributes-by-usage.md)。

### <a name="repeatable"></a>可重複

此欄位會指出是否將屬性可以重複套用至相同的目標。 大部分的屬性不是可重複的。

### <a name="required-attributes"></a>必要屬性

此欄位會列出其他要使用的屬性才能正確執行指定之屬性的存在 （亦即，套用至相同的目標）。 是常見的此欄位的任何項目屬性。

### <a name="invalid-attributes"></a>無效的屬性

此欄位會列出與指定的屬性不相容的其他屬性。 是常見的此欄位的任何項目屬性。

## <a name="in-this-section"></a>本節內容

[屬性程式設計常見問題集](attribute-programming-faq.md)<br/>
[依群組分類的屬性](attributes-by-group.md)<br/>
[依使用方式分類的屬性](attributes-by-usage.md)<br/>
[依字母順序排列的屬性參考](attributes-alphabetical-reference.md)