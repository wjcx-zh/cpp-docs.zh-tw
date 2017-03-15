---
title: "String  (C++ Component Extensions) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "string support with /clr"
  - "/clr compiler option [C++], string support"
ms.assetid: c695f965-9be0-4e20-9661-373bfee6557e
caps.latest.revision: 19
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# String  (C++ Component Extensions)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 編譯器支援 *字串*，其為表示文字為字元序列的物件。  Visual C\+\+ 支援字串變數\( 其值是隱含的 \)和文字\( 其值是明確的由引號括住的字串 \)。  
  
## 所有執行階段  
 Windows 執行階段和 Common Language Runtime 表示字串為其配置記憶體自動處理的物件。  也就是說，當字串變數超出範圍或應用程式結束時，不需要明確捨棄字串的記憶體。  表示字串物件的存留期會自動處理，請搭配 [handle\-to\-object \(^\)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md) 修飾詞宣告字串型別。  
  
## Windows 執行階段  
 Windows 執行階段結構需要 Visual C\+\+ 實作在 `Platform` 命名空間中的 `String` 資料型別。  為您的方便， Visual C\+\+ 也提供在 `default` 命名空間的 `string` 資料型別，是 `Platform::String`的同義字。  
  
### 語法  
  
```cpp  
  
// compile with /ZW  
using namespace Platform;  
using namespace default;  
   Platform::String^ MyString1 = "The quick brown fox";  
   String^ MyString2 = "jumped over the lazy dog.";  
   String^ MyString3 = "Hello, world!";  
  
```  
  
### 備註  
 如需字串的詳細資訊與範例，請參閱[Platform::String, std::wstring, and Literals \(Platform\)](http://msdn.microsoft.com/zh-tw/ec92fbc6-edf3-4137-a85e-8e29bdb857a8)。  
  
### 需求  
 編譯器選項：**\/ZW**  
  
## Common Language Runtime  
 本主題討論當您使用 **\/clr** 編譯器選項執行它時， Visual C\+\+ 編譯器如何處理字串常值。  若要使用 **\/clr**，您也必須使用 Common Language Runtime \(CLR\)、C\+\+\/CLI 語法和 Managed 物件。  如需 **\/clr** 的詳細資訊，請參閱 [\/clr \(Common Language Runtime 編譯\)](../build/reference/clr-common-language-runtime-compilation.md)。  
  
 在以 **\/clr**編譯時，編譯器會將字串常值轉換為型別為 <xref:System.String> 的字串。  若要儲存現有程式碼的回溯相容性 \(Backward Compatibility\) ，有兩個例外狀況：  
  
-   例外狀況處理。  當字串常值擲回，編譯器會攔截它做為字串常值。  
  
-   範本推算。  當字串常值被當做樣板引數傳遞，編譯器不會將它轉換成 <xref:System.String>。  請注意，做為泛型引數傳遞的字串常值會提升為 <xref:System.String>。  
  
 編譯器也有內建支援三個運算子，您可以覆寫自訂其行為：  
  
-   System::String ^ operator \+\( System::String, System::String\);  
  
-   System::String ^ operator \+\( System::Object, System::String\);  
  
-   System::String ^ operator \+\( System::String, System::Object\);  
  
 當傳遞 <xref:System.String> 時，編譯器會在必要時分隔然後串連物件 \(用 ToString\(\)\) 的字串。  
  
 在以 **\/clr:oldSyntax** 編譯時，字串常值不會轉換成 <xref:System.String>。  
  
> [!NOTE]
>  插入號 \(^\) 表示宣告的變數是控制代碼 C\+\+\/CLI Managed 物件。  
  
 如需詳細資訊，請參閱[字串和字元常值](../cpp/string-and-character-literals-cpp.md)。  
  
### 需求  
 編譯器選項：**\/clr**  
  
### 範例  
 **範例**  
  
 下列程式碼範例示範串連和比較字串。  
  
```cpp  
// string_operators.cpp  
// compile with: /clr  
// In the following code, the caret ("^") indicates that the   
// declared variable is a handle to a C++/CLI managed object.  
using namespace System;  
  
int main() {  
   String ^ a = gcnew String("abc");  
   String ^ b = "def";   // same as gcnew form  
   Object ^ c = gcnew String("ghi");  
  
   char d[100] = "abc";  
  
   // variables of System::String returning a System::String  
   Console::WriteLine(a + b);  
   Console::WriteLine(a + c);  
   Console::WriteLine(c + a);  
  
   // accessing a character in the string  
   Console::WriteLine(a[2]);  
  
   // concatenation of three System::Strings  
   Console::WriteLine(a + b + c);  
  
   // concatenation of a System::String and string literal  
   Console::WriteLine(a + "zzz");  
  
   // you can append to a System::String ^  
   Console::WriteLine(a + 1);  
   Console::WriteLine(a + 'a');  
   Console::WriteLine(a + 3.1);  
  
   // test System::String ^ for equality  
   a += b;  
   Console::WriteLine(a);  
   a = b;  
   if (a == b)  
      Console::WriteLine("a and b are equal");  
  
   a = "abc";  
   if (a != b)  
      Console::WriteLine("a and b are not equal");  
  
   // System:String ^ and tracking reference  
   String^% rstr1 = a;  
   Console::WriteLine(rstr1);  
  
   // testing an empty System::String ^  
   String ^ n;  
   if (n == nullptr)  
      Console::WriteLine("n is empty");  
}  
```  
  
 **Output**  
  
  **abcdef**  
 **abcghi**  
 **ghiabc**  
 **c**  
 **abcdefghi**  
 **abczzz**  
 **abc1**  
 **abc97**  
 **abc3.1**  
 **abcdef**  
 **a and b are equal**  
 **a and b are not equal**  
 **abc**  
 **n is empty** **範例**  
  
 下列範例顯示，您可以多載編譯器提供的運算子，因此，編譯器會根據 <xref:System.String> 型別找到函式多載。  
  
```cpp  
// string_operators_2.cpp  
// compile with: /clr  
using namespace System;  
  
// a string^ overload will be favored when calling with a String  
void Test_Overload(const char * a) {   
   Console::WriteLine("const char * a");   
}  
void Test_Overload(String ^ a) {   
   Console::WriteLine("String ^ a");   
}  
  
// overload will be called instead of compiler defined operator  
String ^ operator +(String ^ a, String ^ b) {  
   return ("overloaded +(String ^ a, String ^ b)");  
}  
  
// overload will be called instead of compiler defined operator  
String ^ operator +(Object ^ a, String ^ b) {  
   return ("overloaded +(Object ^ a, String ^ b)");  
}  
  
// overload will be called instead of compiler defined operator  
String ^ operator +(String ^ a, Object ^ b) {  
   return ("overloaded +(String ^ a, Object ^ b)");  
}  
  
int main() {  
   String ^ a = gcnew String("abc");  
   String ^ b = "def";   // same as gcnew form  
   Object ^ c = gcnew String("ghi");  
  
   char d[100] = "abc";  
  
   Console::WriteLine(a + b);  
   Console::WriteLine(a + c);  
   Console::WriteLine(c + a);  
  
   Test_Overload("hello");  
   Test_Overload(d);  
}  
```  
  
 **Output**  
  
  **overloaded \+\(String ^ a, String ^ b\)**  
 **overloaded \+\(String ^ a, Object ^ b\)**  
 **overloaded \+\(Object ^ a, String ^ b\)**  
 **String ^ a**  
 **const char \* a** **範例**  
  
 下列範例顯示，編譯器原生字串和 <xref:System.String> 字串之間的不同。  
  
```cpp  
// string_operators_3.cpp  
// compile with: /clr  
using namespace System;  
int func() {  
   throw "simple string";   // const char *  
};  
  
int func2() {  
   throw "string" + "string";   // returns System::String  
};  
  
template<typename T>  
void func3(T t) {  
   Console::WriteLine(T::typeid);  
}  
  
int main() {  
   try {  
      func();  
   }  
   catch(char * e) {  
      Console::WriteLine("char *");  
   }  
  
   try {  
      func2();  
   }  
   catch(String^ str) {  
      Console::WriteLine("String^ str");  
   }  
  
   func3("string");   // const char *  
   func3("string" + "string");   // returns System::String  
}  
```  
  
 **Output**  
  
  **char\***  
 **String^ str**  
 **System.SByte\***  
 **System.String**   
## 請參閱  
 [Component Extensions for Runtime Platforms](../windows/component-extensions-for-runtime-platforms.md)   
 [字串和字元常值](../cpp/string-and-character-literals-cpp.md)   
 [\/clr \(Common Language Runtime 編譯\)](../build/reference/clr-common-language-runtime-compilation.md)