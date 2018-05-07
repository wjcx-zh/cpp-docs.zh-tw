---
title: CLR 列舉型別 |Microsoft 文件
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
ms.openlocfilehash: 2416a306373db08c5e925b4987fc8a9273973c39
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="clr-enum-type"></a>CLR 列舉類型
宣告和列舉的行為已變更從 Managed Extensions for c + + 為 Visual c + +。  
  
 Managed Extensions 列舉宣告加`__value`關鍵字。 這裡的做法是原生列舉區別衍生自 CLR 列舉`System::ValueType`，同時建議類似的功能。 例如:   
  
```  
__value enum e1 { fail, pass };  
public __value enum e2 : unsigned short  {   
   not_ok = 1024,   
   maybe, ok = 2048   
};  
```  
  
 新語法能夠解決的問題區別原生和 CLR 列舉強調類別本質，後者而不是其值類型的根。 因此，`__value`關鍵字會捨棄，取代之間距的關鍵字字組`enum class`。 這會提供一組的關鍵字對稱，宣告的參考、 值和介面的類別：  
  
```  
enum class ec;  
value class vc;  
ref class rc;  
interface class ic;  
```  
  
 列舉組翻譯`e1`和`e2`新語法中看起來像這樣：  
  
```  
enum class e1 { fail, pass };  
public enum class e2 : unsigned short {   
   not_ok = 1024,  
   maybe, ok = 2048   
};  
```  
  
 這個小語法變更，除了 CLR 列舉型別的行為已變更在數種方式：  
  
-   不再支援 CLR 列舉的向前宣告。 沒有對應。 它只被標示為編譯時期錯誤。  
  
```  
__value enum status; // Managed Extensions: ok  
enum class status;   // new syntax: error  
```  
  
-   內建算術類型之間的多載解析和`Object`類別階層有兩種語言版本之間回復 ！ 副作用，CLR 列舉會不再隱含轉換成算術類型。  
  
-   在新語法中，CLR 列舉會維持其本身的範圍，這不是這樣，在 Managed Extensions。 列舉值之前，在包含列舉的範圍內為可見。 現在，列舉值會封裝在列舉的範圍內。  
  
## <a name="clr-enums-are-a-kind-of-object"></a>CLR 列舉是種類型的物件  
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
  
 為原生 c + + 程式設計人員，自然問題的解答的哪一個執行個體的多載`f()`叫用時，就是`f(int)`。 Enum 符號的整數常數，並參與標準整數提升會優先考慮在此情況下。  但事實上在 Managed Extensions 此呼叫會解析的執行個體。 不會在我們會用它們在原生 c + + 的心態-，但我們需要其現有的 BCL （基底類別程式庫） 架構，與互動時，這會造成意外-一些其中`Enum`類別間接衍生自`Object`。 在 Visual c + + 語言設計的執行個體`f()`叫用，就是`f(Object^)`。  
  
 Visual c + + 已選擇強制執行此方法是不支援 CLR 列舉型別與算術類型之間的隱含轉換。 這表示任何算術類型的 CLR 列舉型別物件的指派，將會要求明確轉換。 因此，例如，假設  
  
```  
void f( int );  
```  
  
 做為非多載方法，在 Managed Extensions，呼叫  
  
```  
f( rslt ); // ok: Managed Extensions; error: new syntax  
```  
  
 [確定]，內含的值`rslt`會隱含地轉換成整數值。 在 Visual c + + 中，這個呼叫會無法編譯。 若要正確地轉譯，我們必須插入轉換運算子：  
  
```  
f( safe_cast<int>( rslt )); // ok: new syntax  
```  
  
## <a name="the-scope-of-the-clr-enum-type"></a>CLR 列舉類型的範圍  
 其中一個 C 和 c + + 語言之間的變更是範圍的 c + + 中加入內的結構設備。 在 C 中，結構是只將資料彙總不支援的介面或相關聯的範圍。 這是相當多的字根的改變，而是許多新的 c + + 使用者來自 C 語言的競爭問題。 原生和 CLR 列舉之間的關聯性是類似。  
  
 在 Managed Extensions，嘗試以模擬的範圍中的原生列舉沒有定義的 CLR 列舉的列舉值的弱式插入的名稱。 這不經過證明成功。 問題是，這會使列舉值落入全域命名空間，導致難以管理名稱衝突。 在新語法中，我們已符合其他 CLR 語言支援範圍中 CLR 列舉。  
  
 這表示任何 CLR 列舉的列舉值的非限定的使用無法辨識以新的語法。 讓我們看看真實世界範例。  
  
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
  
 每個不合格的三個使用的列舉值名稱 (`(1)`， `(2)`，和`(3)`) 必須限定在新語法編譯原始程式碼的順序轉譯。 以下是正確的原始來源程式碼翻譯：  
  
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
  
 這樣會變更為原生和 CLR 列舉之間的設計策略。 CLR 列舉維護相關聯的範圍，在 Visual c + + 中，是不必要也不有效封裝列舉類別內的宣告。 這個慣用語是 cfront 2.0 鈴鐺實驗室內的時間也才能解決全域名稱侵害。  
  
 在鈴鐺 Laboratories Jerry Schwarz 新 iostream 程式庫的原始 beta 版，Jerry 未封裝所有相關聯的列舉定義的程式庫和一般的列舉程式，例如`read`， `write`， `append`，依此類推即幾乎不可能讓使用者在其現有的程式碼編譯。 一個方案就已經名稱，例如弄亂`io_read`，`io_write`等等。第二個方案也已經修改語言將範圍加入至列舉，但這不是可行的作法時。 中間的方案是封裝的列舉類別或類別階層中，標記名稱與列舉的列舉值填入封閉類別範圍）。也就是說，至少一開始放置在類別中，列舉的動機未明智，但全域命名空間的侵害問題的實際回應。  
  
 Visual c + + 列舉，具有不再封裝列舉類別內任何令人信服的好處。 事實上，如果您看一下`System`命名空間，您會看到該列舉、 類別和介面全都位於相同的宣告空間。  
  
## <a name="see-also"></a>另請參閱  
 [實值類型和它們的行為 (C + + /CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)   
 [列舉類別](../windows/enum-class-cpp-component-extensions.md)