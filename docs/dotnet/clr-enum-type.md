---
title: "CLR 列舉類型 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "enum class 關鍵字 [C++]"
  - "enum struct 關鍵字 [C++]"
  - "範圍, CLR enum 的"
ms.assetid: 4541d952-97bb-4e35-a7f8-d14f5f6a6606
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CLR 列舉類型
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從 Managed Extensions for C\+\+ 升級為 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 之後，列舉的宣告和行為已變更。  
  
 Managed Extensions 列舉宣告之前必須搭配 `__value` 關鍵字。  此處的要點是能分辨原生 \(Native\) 列舉和衍生自 `System::ValueType` 的 CLR 列舉，同時也建議類似的功能。  例如：  
  
```  
__value enum e1 { fail, pass };  
public __value enum e2 : unsigned short  {   
   not_ok = 1024,   
   maybe, ok = 2048   
};  
```  
  
 新語法解決原生和 CLR 列舉之間分辨問題的方法，是強調後者的類別本質，而非實值型別根項目。  因此會捨棄 `__value` 關鍵字，改用一組間隔關鍵字 `enum class` 取代。  這種做法會提供一組關鍵字對稱給參考、實值和介面類別的宣告：  
  
```  
enum class ec;  
value class vc;  
ref class rc;  
interface class ic;  
```  
  
 在新語法中，列舉型別組 `e1` 和 `e2` 轉譯如下所示：  
  
```  
enum class e1 { fail, pass };  
public enum class e2 : unsigned short {   
   not_ok = 1024,  
   maybe, ok = 2048   
};  
```  
  
 除了這個小小的語法變更以外，CLR 列舉型別的行為在不同方面也有所變更：  
  
-   不再支援 CLR 列舉的向前宣告。  沒有對應，  只是將它標示為編譯時期錯誤。  
  
```  
__value enum status; // Managed Extensions: ok  
enum class status;   // new syntax: error  
```  
  
-   內建算術型別和 `Object` 類別階層之間的多載解析，已於兩種語言版本之間回復！  副作用是，CLR 列舉無法再隱含地轉換成算術型別。  
  
-   在新語法中，CLR 列舉會維護本身的範圍，但在 Managed Extensions 則不是如此。  以前，在列舉的包含範圍內看得到列舉值。  現在，列舉值則封裝於列舉範圍內。  
  
## CLR 列舉是一種物件  
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
  
 對於原生 C\+\+ 的程式設計人員而言，叫用多載的 `f()` 執行個體就是 `f(int)` 的執行個體。  列舉是符號整數常數，而且它會參與在此情況下會優先考慮的標準整數提升。而且實際上在 Managed Extensions 中，這是呼叫要解析的執行個體。  這樣會製造一些驚喜，不是刻意在原生 C\+\+ 框架 \(Frame\) 中使用時，而是當需要用來和現有的 BCL \(基底類別庫\) 架構互動時，其中 `Enum` 是間接衍生自 `Object` 的類別。  在 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 語言設計中，所叫用之 `f()` 的執行個體是 `f(Object^)` 的執行個體。  
  
 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 選擇用來強制施行的方式，是不支援 CLR 列舉型別和算術型別之間的隱含轉換。  這表示將任何 CLR 列舉型別物件指派至算數型別時，需要明確的轉換 \(Cast\)。  所以比方說指定  
  
```  
void f( int );  
```  
  
 做為非多載方法時，在 Managed Extensions 中可以呼叫  
  
```  
f( rslt ); // ok: Managed Extensions; error: new syntax  
```  
  
 ，而且 `rslt` 中內含的值會隱含地轉換為整數值。  在 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 中編譯這項呼叫時則會失敗。  若要正確地轉譯，則必須插入轉換運算子：  
  
```  
f( safe_cast<int>( rslt )); // ok: new syntax  
```  
  
## CLR 列舉型別的範圍  
 C 和 C\+\+ 語言之間的其中一項改變，就是在 C\+\+ 中增加結構 \(Struct\) 機能的範圍。  在 C 中，結構只是缺少介面或相關範圍支援的資料彙總 \(Aggregate\)。  這在當時是一項很根本的改變，而且對於許多剛從 C 語言改用 C\+\+ 的新使用者而言是個會引起爭議的問題。  原生和 CLR 列舉之間的關係很相似。  
  
 在 Managed Extensions 中，會嘗試針對 CLR 列舉的列舉值定義弱式插入名稱，以便在原生列舉中模擬缺少範圍的情況。  這樣做不保證一定能成功。  問題在於這種做法會使列舉值落入全域命名空間，導致很難管理名稱衝突。  在新語法中，則已符合 CLR 列舉的支援範圍中的其他 CLR 語言。  
  
 也就是說，如果不是以合格方式使用 CLR 列舉的列舉值，新語法就無法辨認此值。  我們來看看實際範例。  
  
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
  
      // here are the problems …  
      optionList->Add(S"?", __box(OPTION_USAGE)); // (1)  
      optionList->Add(S"help", __box(OPTION_USAGE)); // (2)  
  
      itagList = new ListDictionary;  
      itagList->Add(S"returns",   
         __box(XDC0004_WRN_XML_LOAD_FAILURE)); // (3)  
   }  
};  
```  
  
 對於下列三種資格不符的列舉值名稱用法而言 \(亦即 `(1)`、`(2)` 和 `(3)`\)，每一種都需要在轉譯至新語法的程序中定義為合格，如此才能編譯原始程式碼。  下列是原本的原始程式碼的正確轉譯：  
  
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
  
 這樣會改變原生和 CLR 列舉之間的設計策略。  在 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 中使用 CLR 列舉維護相關範圍時，於類別中封裝列舉宣告是不必要也是無效的做法。  這個慣用語是在貝爾實驗室研發 cfront 2.0 時逐漸形成，同時也是用來解決全域名稱干擾問題。  
  
 在貝爾實驗室中，由 Jerry Schwarz 所研發的新 iostream 程式庫的原始 Beta 版中，Jerry 並未封裝所有針對實驗室所定義的相關列舉，而且 `read`、`write`、`append` 等一般列舉值讓使用者幾乎不可能編譯現有程式碼。  一個解決方法是破壞名稱，例如 `io_read`、 `io_write` 等等。第二個解決方法藉由將範圍加入至列舉，以修改語言，但這在當時是行不通的。  而居中的解決方法則是封裝類別中的列舉或類別階層，其中列舉的標記名稱和列舉值都會填入 \(Populate\) 封入類別 \(Enclosing Class\) 範圍。換句話說，在類別中放置列舉的動機在當初看來不明智，但卻是因應全域命名空間干擾問題的可行做法。  
  
 有了 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 列舉，在類別中封裝列舉就再也沒有任何值得讚賞的優點了。  事實上，如果查看 `System` 命名空間，將會看到列舉、類別和介面全都位於相同的宣告空間中。  
  
## 請參閱  
 [實值類型和行為 \(C\+\+\/CLI\)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)   
 [enum class](../windows/enum-class-cpp-component-extensions.md)