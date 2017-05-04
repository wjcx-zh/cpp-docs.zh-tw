---
title: "字串 (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "01/22/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5b34e1df-7c2b-4269-aba8-b767d36c49d9
caps.latest.revision: 22
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 22
---
# 字串 (C++/CX)
[!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]中的文字在 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 中會以 [Platform::String 類別](../cppcx/platform-string-class.md) 表示。 當您對 `Platform::String Class`類別中的方法傳入或傳出字串時，或是跨應用程式二進位介面 \(ABI\) 界限與其他 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]元件互動時，請使用 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]。`Platform::String Class` 提供適用於幾個常見字串作業的方法，但它並不是針對完整功能的字串類別而設計的。 您可以在 C\+\+ 模組中使用 Standard C\+\+ 字串型别 \(如 [wstring](http://msdn.microsoft.com/library/77953dd7-ee2f-4f6c-90e7-27da549ca631)\) 進行任何重要的文字處理，然後將最終的結果轉換成 [Platform::String^](../cppcx/platform-string-class.md)，再將其傳入或傳出公用介面。`wstring` 或 `wchar_t*` 與 `Platform::String` 之間可進行簡單而有效的轉換。  
  
 **快速傳遞**  
  
 在某些情況下，編譯器可確認無需先行複製基礎字串資料，即可安全地建構 `Platform::String` 或將 `String` 傳遞至函式。 這類作業稱為「*快速傳遞*」\(Fast Pass\)，可以明確地執行。  
  
## 字串建構  
 `String` 物件的值是 `char16` \(16 位元 Unicode\) 字元不可變的 \(唯讀\) 序列。 由於 `String` 物件是不可變的，因此在指派新的字串常值指派給 `String` 變數後，即會將原始的 `String` 物件取代為新的 `String` 物件。 串連作業包含原始 `String` 物件的解構與新物件的建立。  
  
 **常值**  
  
 「*常值字元*」\(Literal Character\) 是包含在單引號中的字元，而「*常值字串*」\(Literal String\) 則是包含在雙引號中的字元序列。 如果您使用常值初始化 String^ 變數，編譯器會假設常值包含 `char16` 字元。 也就是說，您無需在常值之前加上 'L' 字串修飾詞，或是將常值納入 **\_T\(\)** 或 **TEXT\(\)** 巨集中。 如需 C\+\+ 之 Unicode 支援的詳細資訊，請參閱 [Unicode 程式設計摘要](../text/unicode-programming-summary.md)。  
  
 下列範例說明各種建構 `String` 物件的方式。  
  
 [!code-cpp[cx_strings#01](../snippets/cpp/VS_Snippets_Misc/cx_strings/cpp/class1.cpp#01)]  
  
## 字串處理作業  
 `String` 類別會提供串連字串、比較字串與其他基本字串作業所需的方法與運算子。 若要執行更廣泛的字串管理，請使用 `String::Data()` 成員函式來擷取 `String^` 物件的值，做為 `const wchar_t*`。 接著請使用該值初始化 `std::wstring`，以提供多樣化的字串處理函式。  
  
 [!code-cpp[cx_strings#03](../snippets/cpp/VS_Snippets_Misc/cx_strings/cpp/class1.cpp#03)]  
  
## 字串轉換  
 `Platform::String` 只能包含 `char16` 字元或 `NULL` 字元。 如果您的應用程式必須使用 8 位元字元，請使用 [String::Data 方法](../cppcx/string-data-method.md) 擷取文字，做為 `const wchar_t*`。 接著，您可以使用適當的 Windows 函式或標準程式庫函式來處理資料，並將其重新轉換成 `wchar_t*` 或 [wstring](http://msdn.microsoft.com/library/77953dd7-ee2f-4f6c-90e7-27da549ca631)，供您用以建構新的 `Platform::String`。  
  
 下列程式碼片段說明如何在 `String^` 變數與 `wstring` 變數之間轉換。 如需此範例中使用之字串操作的詳細資訊，請參閱 [basic\_string::replace](http://msdn.microsoft.com/library/16d81b9d-9724-458a-9179-556748034507)。  
  
 [!code-cpp[cx_strings#04](../snippets/cpp/VS_Snippets_Misc/cx_strings/cpp/class1.cpp#04)]  
  
## 字串長度與內嵌的 NULL 值  
 [String::Length 方法](../cppcx/string-length-method.md) 會傳回字串中的字元數，而不是位元組數。 結尾的 NULL 字元不會計入字元數，除非您在使用堆疊語意建構字串時明確加以指定。  
  
 `Platform::String` 可包含內嵌 NULL 值，但僅限於 NULL 是串連作業的結果時。 字串常值不支援內嵌 NULL，因此您無法以該格式使用內嵌 NULL 初始化 `Platform::String`。 字串顯示時，`Platform::String` 中的內嵌 NULL 值會被忽略，例如在字串指派給 `TextBlock::Text` 屬性時。`Data` 屬性傳回字串值時，會移除內嵌的 NULL。  
  
## StringReference  
 在某些情況下，您的程式碼 \(a\) 會接收 std::wstring 或 wchar\_t 字串或 L”” 字串常值，然後直接將它傳遞至可接受 String^ 做為輸入參數的其他方法。 只要原始字串緩衝區保持有效，而且在函式傳回前不會變動，您可以將 `wchar_t*` 字串或字串常值轉換成 [Platform::StringReference](../cppcx/platform-stringreference-class.md)，並傳入後者而不傳入 `Platform::String^`。 因為 `StringReference` 具有轉換為 `Platform::String^` 的使用者定義轉換，所以允許這個作業。 使用 `StringReference`，可以避免建立字串資料的額外複本。 在傳遞大量字串的迴圈中，或在傳遞非常大型的字串時，透過使用 `StringReference`，效能可能會顯著改善。 但是因為 `StringReference` 基本上借用原始字串緩衝區，您必須非常小心避免記憶體損毀。 除非原始字串在這個方法傳回時保證在範圍內，否則不應該將 `StringReference` 傳遞至非同步方法。 從 StringReference 初始化的 String^ 會在第二個指派作業發生時，強制字串資料的配置和複製。 在這種情況下，將會遺失 `StringReference` 的效能優勢。  
  
 請注意，`StringReference` 是 Standard C\+\+ 類別型別，不是 ref 類別，無法用於您定義的 ref 類別公用介面。  
  
 下列範例示範如何使用 StringReference：  
  
```  
void GetDecodedStrings(std::vector<std::wstring> strings)  
{  
    using namespace Windows::Security::Cryptography;  
    using namespace Windows::Storage::Streams;  
  
    for (auto&& s : strings)  
    {  
        // Method signature is IBuffer^ CryptographicBuffer::DecodeFromBase64String (Platform::String^)  
        // Call using StringReference:  
        IBuffer^ buffer = CryptographicBuffer::DecodeFromBase64String(StringReference(s.c_str()));  
  
        //...do something with buffer  
    }  
}  
```  
  
## 請參閱  
 [Built\-in Types](http://msdn.microsoft.com/zh-tw/acc196fd-09da-4882-b554-6c94685ec75f)