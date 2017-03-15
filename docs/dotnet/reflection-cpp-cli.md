---
title: "反映 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
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
  - ".NET Framework [C++], 反映"
  - "資料類型 [C++], 反映"
  - "GetType 方法"
  - "中繼資料, 反映"
  - "反映 [C++]"
  - "反映 [C++], 關於反映"
  - "typeid 關鍵字 [C++]"
ms.assetid: 46b6ff4a-e441-4022-8892-78e69422f230
caps.latest.revision: 24
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 反映 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

反映 \(Reflection\) 允許在執行階段檢查已知的資料型別。  反映允許指定組件中資料型別列舉，並且會發現指定類別的成員或實值型別。  不管該型別是已知的或者在編譯時才參考的，它都會這樣做。  這樣會讓反映成為開發及程式碼管理工具的有用功能。  
  
 請注意，提供的組件名稱為強式名稱 \(請參閱[強式名稱的組件](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md)\)，其中包括組件版本、文化特性和簽章資訊。  同時也請注意，可以在擷取基底類別名稱時一起擷取命名空間的名稱 \(資料型別是在此命名空間中定義的\)。  
  
 存取反映功能最常用的方式就是透過 <xref:System.Object.GetType%2A> 方法。  這個方法是由 [System::Object](https://msdn.microsoft.com/en-us/library/system.object.aspx) 提供，所有的記憶體回收類別也衍生於此。  
  
 如果使用 **\/clr:pure** 或 **\/clr:safe** 編譯器選項建置 .exe，則在以 Visual C\+\+ 編譯器建置的 .exe 上允許反映。  如需詳細資訊，請參閱[\/clr \(Common Language Runtime 編譯\)](../build/reference/clr-common-language-runtime-compilation.md)。  
  
 本節主題：  
  
-   [如何：使用反映實作外掛程式元件架構](../dotnet/how-to-implement-a-plug-in-component-architecture-using-reflection-cpp-cli.md)  
  
-   [如何：使用反映以列舉組件中的資料類型](../dotnet/how-to-enumerate-data-types-in-assemblies-using-reflection-cpp-cli.md)  
  
 如需詳細資訊，請參閱 [System.Reflection 命名空間](https://msdn.microsoft.com/en-us/library/system.reflection.aspx)。  
  
## 範例  
 `GetType` 方法會傳回 <xref:System.Type> 類別物件的指標，此指標會描述所依據之物件的型別\(**Type** 物件不包含任何特定執行個體的資訊\)。這樣的項目即是該型別的完整名稱，可顯示如下：  
  
 請注意，型別名稱包括定義型別的完整範圍 \(包含命名空間\)，而且它是以 .NET 語法顯示 \(含有做為範圍解析運算子的點\)。  
  
```  
// vcpp_reflection.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   String ^ s = "sample string";  
   Console::WriteLine("full type name of '{0}' is '{1}'", s, s->GetType());  
}  
```  
  
  **'sample string' 的完整類型名稱是 'System.String'**   
## 範例  
 實值型別也可以與 `GetType` 函式一起使用，但必須先執行 box 動作。  
  
```  
// vcpp_reflection_2.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   Int32 i = 100;   
   Object ^ o = i;  
   Console::WriteLine("type of i = '{0}'", o->GetType());  
}  
```  
  
  **i 的型別 \= 'System.Int32'**   
## 範例  
 如果使用 `GetType` 方法，[typeid](../windows/typeid-cpp-component-extensions.md) 運算子會將指標傳回至 \[**Type**\] 物件，因此這項程式碼會指出型別名稱 **System.Int32**。  顯示型別名稱是反映的最基本功能，但是反映還具備另一項可能更有用的技術，就是檢查或探索 \(Discover\) 列舉型別的有效值。  若要達成此目的，可以使用靜態 **Enum::GetNames** 函式，它會傳回字串陣列，在文字表單中每個字串都包含列舉值。下列範例會擷取字串陣列 \(該字串描述 \[**Options**\] \(CLR\) 列舉的列舉值\)，並在迴圈中顯示它們。  
  
 如果第四個選項加入至 \[**Options**\] 列舉型別，此程式碼將會報告新選項而不會重新編譯，即使列舉型別是在其他組件中定義的也一樣。  
  
```  
// vcpp_reflection_3.cpp  
// compile with: /clr  
using namespace System;  
  
enum class Options {   // not a native enum  
   Option1, Option2, Option3  
};  
  
int main() {  
   array<String^>^ names = Enum::GetNames(Options::typeid);  
  
   Console::WriteLine("there are {0} options in enum '{1}'",   
               names->Length, Options::typeid);  
  
   for (int i = 0 ; i < names->Length ; i++)  
      Console::WriteLine("{0}: {1}", i, names[i]);  
  
   Options o = Options::Option2;  
   Console::WriteLine("value of 'o' is {0}", o);  
}  
```  
  
  **在 'Options' 列舉中有 3 個選項**  
**0: Option1**  
**1: Option2**  
**2: Option3**  
**'o' 的值是 Option2**   
## 範例  
 `GetType` 物件支援許多成員和用來檢查型別的屬性。  此程式碼會擷取並顯示一些資訊：  
  
```  
// vcpp_reflection_4.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   Console::WriteLine("type information for 'String':");  
   Type ^ t = String::typeid;  
  
   String ^ assemblyName = t->Assembly->FullName;  
   Console::WriteLine("assembly name: {0}", assemblyName);  
  
   String ^ nameSpace = t->Namespace;  
   Console::WriteLine("namespace: {0}", nameSpace);  
  
   String ^ baseType = t->BaseType->FullName;  
   Console::WriteLine("base type: {0}", baseType);  
  
   bool isArray = t->IsArray;  
   Console::WriteLine("is array: {0}", isArray);  
  
   bool isClass = t->IsClass;  
   Console::WriteLine("is class: {0}", isClass);  
}  
```  
  
  **'String' 的型別資訊：**  
**組譯碼名稱: mscorlib, Version\=1.0.5000.0, 文化特性\=neutral,**  
**PublicKeyToken\=b77a5c561934e089**  
**命名空間：System**  
**基底類型: System.Object**  
**是陣列：False**  
**是類別： True**   
## 範例  
 反映也允許組件內可以有列舉型別和類別內可以有成員。  若要示範此功能，請定義簡單類別：  
  
```  
// vcpp_reflection_5.cpp  
// compile with: /clr /LD  
using namespace System;  
public ref class TestClass {  
   int m_i;  
public:  
   TestClass() {}  
   void SimpleTestMember1() {}  
   String ^ SimpleMember2(String ^ s) { return s; }   
   int TestMember(int i) { return i; }  
   property int Member {  
      int get() { return m_i; }  
      void set(int i) { m_i = i; }  
   }  
};  
```  
  
## 範例  
 如果將上述程式碼編譯至名為 vcpp\_reflection\_6.dll 的 DLL，就可以使用反映檢查此組件的內容。  這牽涉到使用靜態反映 API 函式 [Assembly::Load](https://msdn.microsoft.com/en-us/library/system.reflection.assembly.load.aspx) 以載入組件，  這個函式會傳回 **Assembly** 物件的位址，之後便可在其內查詢物件的模組和型別。  
  
 一旦反映系統成功地載入組件，就會以 [Assembly::GetTypes](https://msdn.microsoft.com/en-us/library/system.reflection.assembly.gettypes.aspx) 函式擷取 \[**Type**\] 物件陣列。  每個陣列元素都會包含不同型別的相關資訊 \(即使在這個範例中只定義一個類別\)。  若使用迴圈，就可使用 **Type::GetMembers** 函式查詢此陣列中每個 **Type** 的型別成員。  這個函式會傳回 **MethodInfo** 物件陣列，其中每個物件都包含成員函式、資料成員或型別屬性 \(Property\) 的相關資訊。  
  
 請注意，方法清單包括 **TestClass** 中明確定義的函式，以及從 **System::Object** 類別中隱含繼承的函式。  由於是用 .NET 而非 Visual C\+\+ 語法來描述的部分，屬性 \(Property\) 會顯示為基礎資料成員，須以 get\/set 函式來存取。  get\/set 函式會以規則性方法出現在此清單中。  反映的支援不是透過 Visual C\+\+ 編譯器，而是透過 Common Language Runtime。  
  
 雖然可以使用此程式碼檢查所定義的組件，但是也可以使用此程式碼檢查 .NET 組件。  例如，如果您將 TestAssembly 變更為 mscorlib，您將會看到 mscorlib.dll 中定義的各種型別和方法的清單。  
  
```  
// vcpp_reflection_6.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::IO;  
using namespace System::Reflection;  
int main() {  
   Assembly ^ a = nullptr;  
   try {  
      // load assembly -- do not use file extension  
      // will look for .dll extension first  
      // then .exe with the filename  
      a = Assembly::Load("vcpp_reflection_5");  
   }  
   catch (FileNotFoundException ^ e) {  
      Console::WriteLine(e->Message);  
      return -1;  
   }  
  
   Console::WriteLine("assembly info:");  
   Console::WriteLine(a->FullName);  
   array<Type^>^ typeArray = a->GetTypes();  
  
   Console::WriteLine("type info ({0} types):", typeArray->Length);  
  
   int totalTypes = 0;  
   int totalMembers = 0;  
   for (int i = 0 ; i < typeArray->Length ; i++) {  
      // retrieve array of member descriptions  
      array<MemberInfo^>^ member = typeArray[i]->GetMembers();  
  
      Console::WriteLine("  members of {0} ({1} members):",   
      typeArray[i]->FullName, member->Length);  
      for (int j = 0 ; j < member->Length ; j++) {  
         Console::Write("       ({0})",   
         member[j]->MemberType.ToString() );  
         Console::Write("{0}  ", member[j]);  
         Console::WriteLine("");  
         totalMembers++;  
      }  
      totalTypes++;  
   }  
   Console::WriteLine("{0} total types, {1} total members",  
   totalTypes, totalMembers);  
}  
```  
  
## 請參閱  
 [以 C\+\+\/CLI 進行 .NET 程式設計](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)