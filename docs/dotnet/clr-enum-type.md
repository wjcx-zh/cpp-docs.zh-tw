---
title: CLR 列舉型別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- scope, of CLR enum
- enum struct keyword [C++]
- enum class keyword [C++]
ms.assetid: 4541d952-97bb-4e35-a7f8-d14f5f6a6606
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a39c451bcff7b5b3b1d7dd9f0d3925616b9d6aab
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436220"
---
# <a name="clr-enum-type"></a>CLR 列舉類型

宣告和列舉的行為已變更從 Managed Extensions for c + + 為 Visual c + +。

Managed Extensions 的列舉宣告前面加上`__value`關鍵字。 這意思是區別衍生自 CLR 列舉的原生列舉`System::ValueType`，同時建議類似的功能。 例如: 

```
__value enum e1 { fail, pass };
public __value enum e2 : unsigned short  {
   not_ok = 1024,
   maybe, ok = 2048
};
```

新的語法能夠解決區別原生的問題和 CLR 列舉強調類別的本質，後者而不是值類型的起源。 因此，`__value`關鍵字已被丟棄，取代為等間距的關鍵字對`enum class`。 這會提供一組的關鍵字對稱，宣告的參考、 值和介面的類別：

```
enum class ec;
value class vc;
ref class rc;
interface class ic;
```

列舉型別組翻譯`e1`和`e2`新語法中看起來像這樣：

```
enum class e1 { fail, pass };
public enum class e2 : unsigned short {
   not_ok = 1024,
   maybe, ok = 2048
};
```

除了這個小小的語法變更 CLR 列舉型別的行為已變更在數種方式：

- 不再支援的 CLR 列舉之向前宣告。 沒有對應。 它只被標示為編譯時期錯誤。

```
__value enum status; // Managed Extensions: ok
enum class status;   // new syntax: error
```

- 內建算術類型之間的多載解析和`Object`類別階層已反轉之間的兩個語言版本 ！ 副作用，CLR 列舉是無法再隱含地轉換到算術類型。

- 在新語法中，CLR 列舉會維護自己的範圍，不是 Managed Extensions 中的案例。 以往，列舉值都是列舉的可見包含的範圍內。 現在，列舉值會封裝列舉的範圍內。

## <a name="clr-enums-are-a-kind-of-object"></a>CLR 列舉都是種類型的物件

請考慮下列程式碼片段：

```
__value enum status { fail, pass };

void f( Object* ){ Console::WriteLine("f(Object)\n"); }
void f( int ){ Console::WriteLine("f(int)\n"); }

int main()
{
   status rslt = fail;

   f( rslt ); // which f is invoked?
}
```

原生的 c + + 程式設計師，自然問題的解答的哪一個執行個體的多載`f()`叫用時，就是`f(int)`。 列舉是一個符號的整數常數，與它所參與的標準整數提升會優先考慮在此情況下。  但事實上 Managed Extensions 中此呼叫會解析的執行個體。 不會在我們會用它們在原生 c + + 的心態-，但我們需要它們與現有的 BCL （基底類別程式庫） 架構，互動時，這會造成意外-許多地方`Enum`類別間接衍生自`Object`。 在 Visual c + + 語言設計中，執行個體`f()`叫用，就是`f(Object^)`。

Visual c + + 已選擇強制執行這種方式，是不支援 CLR 列舉型別與算術類型之間的隱含轉換。 這表示任何指派的算術類型的 CLR 列舉型別物件，需要明確轉換。 因此，比方說，假設

```
void f( int );
```

設為非多載方法，在受管理的擴充功能，呼叫

```
f( rslt ); // ok: Managed Extensions; error: new syntax
```

[確定]，並內所包含的值是`rslt`會隱含地轉換成整數值。 Visual c + + 中，此呼叫會無法編譯。 若要正確地解譯它，我們必須插入轉換運算子：

```
f( safe_cast<int>( rslt )); // ok: new syntax
```

## <a name="the-scope-of-the-clr-enum-type"></a>CLR 列舉類型的範圍

C 和 c + + 語言之間的變更是範圍的 c + + 中加入的結構設施內。 在 C 中，結構是只將資料彙總不支援的介面或相關聯的範圍。 這是相當巨大的改變，而是來自 C 語言的許多新 c + + 使用者的競爭問題。 原生和 CLR 列舉之間的關聯性很相似。

在受管理的擴充功能，嘗試以模擬的範圍內的原生列舉沒有定義的 CLR 列舉的列舉值的弱式插入的名稱。 這不證明成功。 問題在於這會導致溢出到全域命名空間，導致難以管理名稱發生衝突的列舉值。 在新語法中，我們已符合其他 CLR 語言的支援 CLR 列舉中的範圍。

這表示任何不完整的 CLR 列舉的列舉值使用無法辨識新的語法。 讓我們看看真實世界範例。

```
// Managed Extensions supporting weak injection
__gc class XDCMake {
public:
   __value enum _recognizerEnum {
      UNDEFINED,
      OPTION_USAGE,
      XDC0001_ERR_PATH_DOES_NOT_EXIST = 1,
      XDC0002_ERR_CANNOT_WRITE_TO = 2,
      XDC0003_ERR_INCLUDE_TAGS_NOT_SUPPORTED = 3,
      XDC0004_WRN_XML_LOAD_FAILURE = 4,
      XDC0006_WRN_NONEXISTENT_FILES = 6,
   };

   ListDictionary* optionList;
   ListDictionary* itagList;

   XDCMake() {
      optionList = new ListDictionary;

      // here are the problems...
      optionList->Add(S"?", __box(OPTION_USAGE)); // (1)
      optionList->Add(S"help", __box(OPTION_USAGE)); // (2)

      itagList = new ListDictionary;
      itagList->Add(S"returns",
         __box(XDC0004_WRN_XML_LOAD_FAILURE)); // (3)
   }
};
```

每個不合格的三個使用的列舉程式名稱 (`(1)`， `(2)`，和`(3)`) 必須限定在轉譯至新的語法，為了讓要編譯的原始程式碼。 以下是原始程式碼的正確翻譯：

```
ref class XDCMake {
public:
   enum class _recognizerEnum {
      UNDEFINED, OPTION_USAGE,
      XDC0001_ERR_PATH_DOES_NOT_EXIST = 1,
      XDC0002_ERR_CANNOT_WRITE_TO = 2,
      XDC0003_ERR_INCLUDE_TAGS_NOT_SUPPORTED = 3,
      XDC0004_WRN_XML_LOAD_FAILURE = 4,
      XDC0006_WRN_NONEXISTENT_FILES = 6
   };

   ListDictionary^ optionList;
   ListDictionary^ itagList;

   XDCMake() {
      optionList = gcnew ListDictionary;
      optionList->Add("?",_recognizerEnum::OPTION_USAGE); // (1)
      optionList->Add("help",_recognizerEnum::OPTION_USAGE); //(2)
      itagList = gcnew ListDictionary;
      itagList->Add( "returns",
         _recognizerEnum::XDC0004_WRN_XML_LOAD_FAILURE); //(3)
   }
};
```

這會變更之間的原生和 CLR 列舉的設計策略。 使用 CLR 列舉，用來維護相關聯的範圍，在 Visual c + + 中，就不需要也不有效封裝在類別中列舉的宣告。 這個慣用語是 cfront 2.0 Bell Laboratories 內的時間也才能解決全域名稱侵害。

在新的 iostream 程式庫，透過在 Bell Laboratories Jerry Schwarz 原始 beta 版本中，Jerry 未封裝為程式庫，與這類常見的列舉值定義的所有相關聯的列舉`read`， `write`，`append`等等做為其現有的程式碼編譯的使用者幾乎不可能。 其中一個解決方案會以名稱，例如弄亂`io_read`，`io_write`等等。第二個解決方案已經修改語言將範圍加入至列舉，但這不是可行的作法時。 中間的解決方案是封裝在類別中，列舉或類別階層中，標記名稱和列舉的列舉值填入封閉類別範圍）。也就是說，類別中放置列舉，至少一開始的動機不是哲學，但實際回應給全域命名空間干擾問題。

使用 Visual c + + 列舉中，不再封裝在類別內列舉吸引人的優點。 事實上，如果您看一下`System`命名空間，您會看到該列舉、 類別和介面全都位於相同的宣告空間。

## <a name="see-also"></a>另請參閱

[實值型別及其行為 (C++/CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)<br/>
[列舉類別](../windows/enum-class-cpp-component-extensions.md)