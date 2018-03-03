---
title: "列舉類別 （c + + 元件擴充功能） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 8010fa8c-bad6-45b4-8214-b4db64d7ffe1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 876cab344f1177000f63740ca6c33bc1db1afefe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="enum-class--c-component-extensions"></a>enum class (C++ 元件擴充功能)
在命名空間範圍內宣告列舉，這是使用者定義的類型，由一組稱為列舉值的具名常數所組成。  
  
## <a name="all-runtimes"></a>所有執行階段  
 **備註**  
  
 C++/CX 和 C++/CLI 支援類似於標準 C++ `public enum class` 的 `private enum class` 和 `enum class` ，但另外還加上存取範圍規範。 在 **/clr**下允許 C++11 `enum class` 類型，但是會產生警告 C4472，其目的在於確保您是真的想要 ISO 列舉類型，而不是 C++/CX 和 C++/CLI 類型。 如需有關 ISO 標準 c + +`enum`關鍵字，請參閱[列舉](../cpp/enumerations-cpp.md)。  
  
## <a name="windows-runtime"></a>Windows 執行階段  
 **語法**  
  
```  
  
      access  
      enum class  
      enumeration-identifier  
      [:underlying-type] { enumerator-list } [var];  
accessenum structenumeration-identifier[:underlying-type] { enumerator-list } [var];  
```  
  
 **參數**  
  
 *access*  
 列舉的存取範圍可以是 `public` 或 `private`。  
  
 *列舉識別項*  
 列舉名稱。  
  
 *基礎類型*  
 (選用) 列舉的基礎類型。  
  
 (選用。 Windows 執行階段只） 可以是列舉的基礎型別`bool`， `char`， `char16`， `int16`， `uint16`， `int`， `uint32`， `int64`，或`uint64`。  
  
 *列舉程式清單*  
 列舉程式名稱的逗號分隔清單。  
  
 每個列舉程式都是常數運算式，不是透過編譯器隱含定義，就是藉由標記法 *列舉程式*`=`*常數運算式*。 如以隱含方式定義，第一個列舉程式的值預設為零。 後續每個以隱含方式定義的列舉程式值，都是前一個列舉程式的值 + 1。  
  
 *var*  
 (選用) 列舉類型的變數名稱。  
  
 **備註**  
  
 如需詳細資訊與範例，請參閱 [列舉](http://msdn.microsoft.com/%20library/windows/apps/hh755820.aspx)。  
  
 請注意，如果定義列舉程式值的常數運算式無法以 *基礎類型*表示，編譯器將會發出錯誤訊息。  不過，編譯器不會報告不適合基礎類型之值的錯誤。 例如:   
  
-   如果 *基礎類型* 是數值，而列舉程式指定了該類型的最大值，則無法表示下一個隱含定義之列舉的值。  
  
-   如果 *基礎類型* 是 `bool`，而且隱含定義了兩個以上的列舉程式，則無法表示前兩個列舉程式之後的列舉程式。  
  
-   如果 *基礎類型* 是 `char16`，而列舉值的範圍是從 0xD800 到 0xDFFF，則可以表示這個值。 不過，此值在邏輯上不正確，因為它代表 Unicode surrogate 字組的一半，不應該單獨出現。  
  
### <a name="requirements"></a>需求  
 編譯器選項： **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime 
 **語法**  
  
```  
  
      access  
      enum class  
      name [:type] { enumerator-list } var;  
accessenum structname [:type] { enumerator-list } var;  
```  
  
 **參數**  
  
 `access`  
 列舉的存取範圍。  可以是 **公用** 或 `private`。  
  
 `enumerator-list`  
 列舉的識別項 (列舉程式) 逗號分隔清單。  
  
 `name`  
 列舉名稱。  不允許匿名的 Managed 列舉。  
  
 `type` (選擇性)  
 *識別項*的基礎類型。  這可以是任何純量類型，例如 int、short 或 long 的帶正負號或不帶正負號版本。  也可以是`bool` 或 `char` 。  
  
 `var` (選擇性)  
 列舉類型的變數名稱。  
  
 **備註**  
  
 **列舉類別** 和 **列舉結構** 是相同的宣告。  
  
 有兩種列舉類型：Managed 或 C++/CX 和標準。  
  
 Managed 或 C++/CX 列舉可能定義如下：  
  
```cpp  
public enum class day {sun, mon };  
```  
  
 在語意上相當於：  
  
```cpp  
ref class day {  
public:  
   static const int sun = 0;  
   static const int mon = 1;  
};  
```  
  
 標準列舉可能定義如下：  
  
```cpp  
enum day2 { sun, mon };  
```  
  
 在語意上相當於：  
  
```cpp  
static const int sun = 0;  
static const int mon = 1;  
```  
  
 Managed 列舉程式名稱 (*識別項*) 不會插入已定義列舉的範圍，列舉程式的所有參考都必須是完整的 (*名稱*`::`*識別項*)。  為此，您無法定義匿名的 Managed 列舉。  
  
 標準列舉的列舉程式會以強式方式插入封閉範圍。  也就是說，如果封閉範圍中另有一個符號與列舉程式同名，編譯器就會產生錯誤。  
  
 在 Visual C++ 2002 和 Visual C++ 2003 中，列舉程式是以弱式方式插入 (會顯示在封閉範圍中，除非另有同名的識別項)。  
  
 如果定義了標準 C++ 列舉 (沒有 **class** 或 `struct`)，則使用 **/clr** 編譯會將列舉編譯為 Managed 列舉。  列舉仍擁有 Unmanaged 列舉的語意。  請注意，編譯器會插入 Visual C++ 編譯器可辨識的屬性 `Microsoft::VisualC::NativeEnumAttribute`，以識別程式設計人員使用列舉的目的是要做為原生列舉。  其他編譯器只看得到為 Managed 列舉的標準列舉。  
  
 以 /clr 編譯的具名標準列舉，在組件中會顯示為 Managed 列舉，而且可被任何其他 Managed 編譯器使用。   不過，不具名的標準列舉就不會在組件中公開顯示。  
  
 在 Visual C++ 2002 和 Visual C++ 2003 中，標準列舉在函式參數中用做類型：  
  
```cpp  
// mcppv2_enum.cpp  
// compile with: /clr  
enum E { a, b };  
void f(E) {System::Console::WriteLine("hi");}  
  
int main() {  
   E myi = b;  
   f(myi);  
}  
```  
  
 會以 MSIL 格式發出下列項目當做函式簽章：  
  
```  
void f(int32);  
```  
  
 不過，在目前的編譯器版本中，標準列舉是當做附有 [NativeEnumAttribute] 的 Managed 列舉發出，且以 MSIL 格式發出下列項目當做函式簽章：  
  
```  
void f(E)  
```  
  
 如需有關原生列舉的詳細資訊，請參閱 [C++ 列舉宣告](../cpp/enumerations-cpp.md)。  
  
 如需有關 CLR 列舉的詳細資訊，請參閱：  
  
-   [列舉的基礎類型](../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md)  
  
### <a name="requirements"></a>需求  
 編譯器選項： **/clr**  
  
### <a name="examples"></a>範例  
 **範例**  
  
 遞減  
  
```cpp  
// mcppv2_enum_2.cpp  
// compile with: /clr  
// managed enum  
public enum class m { a, b };  
  
// standard enum  
public enum n { c, d };  
  
// unnamed, standard enum  
public enum { e, f } o;  
  
int main()   
{  
   // consume managed enum  
   m mym = m::b;  
   System::Console::WriteLine("no automatic conversion to int: {0}", mym);  
   System::Console::WriteLine("convert to int: {0}", (int)mym);  
  
   // consume standard enum  
   n myn = d;  
   System::Console::WriteLine(myn);  
  
   // consume standard, unnamed enum  
   o = f;  
   System::Console::WriteLine(o);  
}   
```  
  
 **輸出**  
  
```Output  
no automatic conversion to int: b  
  
convert to int: 1  
  
1  
  
1  
  
```  
  
## <a name="see-also"></a>請參閱  
 [執行階段平台的元件延伸模組](../windows/component-extensions-for-runtime-platforms.md)