---
title: 反映 (C + + /CLI) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- typeid keyword [C++]
- reflection [C++}, about reflection
- metadata, reflection
- GetType method
- .NET Framework [C++], reflection
- data types [C++], reflection
- reflection [C++}
ms.assetid: 46b6ff4a-e441-4022-8892-78e69422f230
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d41d7f627a50dd1a09f4256fbd8448d82c6d5f27
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34705240"
---
# <a name="reflection-ccli"></a>反映 (C++/CLI)

反映可讓您在執行階段檢查已知的資料類型。 反映可讓資料類型的列舉中指定的組件，並可以探索到指定的類別或實值類型的成員。 這是不論是否型別是已知的參考在編譯時期，則為 true。 這可讓反映一個實用的功能，用於開發和程式碼管理工具。

請注意，提供的組件名稱是強式名稱 (請參閱[Creating and using strong-named Assemblies](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies))，其中包含組件版本、 文化特性，以及簽章資訊。 請注意，在其中定義資料類型的命名空間名稱無法擷取，以及基底類別的名稱。

若要存取反映功能最常見的方式是透過<xref:System.Object.GetType%2A>方法。 這個方法由[system:: object](https://msdn.microsoft.com/en-us/library/system.object.aspx)，從衍生所有記憶體回收的類別。

> [!NOTE]
> 使用 Visual c + + 編譯器建置的.exe 的反射才允許使用.exe 所建置 **/clr: pure**或 **/clr: safe**編譯器選項。 **/Clr: pure**和 **/clr: safe**編譯器選項為已被取代，在 Visual Studio 2015 和 Visual Studio 2017 中無法使用。 請參閱[/clr （Common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md)如需詳細資訊。

如需詳細資訊，請參閱[System.Reflection 命名空間](https://msdn.microsoft.com/en-us/library/system.reflection.aspx)

## <a name="example-gettype"></a>範例： GetType

`GetType`方法將指標傳回至<xref:System.Type>類別物件，描述在以物件為基礎的類型。 (**類型**物件不包含任何執行個體的特定資訊。)一個這類項目是屬於型別，可以顯示，如下所示的完整名稱：

請注意，型別名稱包含完整的範圍，其中型別定義，包括命名空間，而且，它會顯示在.NET 語法中，以點號做為範圍解析運算子。

```cpp
// vcpp_reflection.cpp
// compile with: /clr
using namespace System;
int main() {
   String ^ s = "sample string";
   Console::WriteLine("full type name of '{0}' is '{1}'", s, s->GetType());
}
```

```Output
full type name of 'sample string' is 'System.String'
```

## <a name="example-boxed-value-types"></a>範例： boxed 實的值類型

實值型別可以搭配`GetType`函式，但它們必須先 boxed。

```cpp
// vcpp_reflection_2.cpp
// compile with: /clr
using namespace System;
int main() {
   Int32 i = 100; 
   Object ^ o = i;
   Console::WriteLine("type of i = '{0}'", o->GetType());
}
```

```Output
type of i = 'System.Int32'
```

## <a name="example-typeid"></a>範例： typeid

如同`GetType`方法， [typeid](../windows/typeid-cpp-component-extensions.md)運算子將指標傳回至**類型**物件，因此這段程式碼中指出的型別名稱**System.Int32**。 顯示型別名稱是最基本功能反映，但可能更實用的方法是檢查或探索列舉類型的有效值。 作法是使用靜態**enum:: getnames**函式，其傳回字串陣列，每一個都會包含文字格式的列舉值。  下列範例會擷取說明的值列舉值的字串陣列**選項**列舉 (CLR) 並將其顯示在迴圈中。

如果是第四個選項加入至**選項**列舉型別，此程式碼會報告不需重新編譯，即使列舉型別在不同的組件中定義新的選項。

```cpp
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

```Output
there are 3 options in enum 'Options'
0: Option1
1: Option2
2: Option3
value of 'o' is Option2
```

## <a name="example-gettype-members-and-properties"></a>範例： GetType 成員和屬性

`GetType`物件支援的成員和屬性，可以用來檢查類型的數字。 此程式碼會擷取並顯示此資訊的某些部分：

```cpp
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

```Output
type information for 'String':
assembly name: mscorlib, Version=1.0.5000.0, Culture=neutral, 
PublicKeyToken=b77a5c561934e089
namespace: System
base type: System.Object
is array: False
is class: True
```

## <a name="example-enumeration-of-types"></a>類型的範例： 列舉

反映也可讓組件中的型別和成員類別中的列舉型別。 若要示範這項功能，定義簡單的類別：

```cpp
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

## <a name="example-inspection-of-assemblies"></a>組件的範例： 檢查

如果上述程式碼編譯成 DLL 呼叫 vcpp_reflection_6.dll，您可以再使用反映來檢查這個組件的內容。 這涉及到使用靜態反映 API 函數[Assembly::Load](https://msdn.microsoft.com/en-us/library/system.reflection.assembly.load.aspx)載入組件。 此函式傳回的位址**組件**然後可查詢有關模組和類型內的物件。

一旦反映系統成功載入的組件的陣列**類型**與擷取物件[Assembly::GetTypes](https://msdn.microsoft.com/en-us/library/system.reflection.assembly.gettypes.aspx)函式。 雖然只有一個類別定義在此情況下，每個陣列元素會包含不同類型的相關資訊。 使用迴圈，每個**類型**此陣列中查詢使用的型別成員相關**Type::GetMembers**函式。 此函式傳回的陣列**MethodInfo**物件、 每個物件，其中包含成員函式、 資料成員或類型中的屬性的相關資訊。

請注意方法的清單包含明確的函數定義中**TestClass**及函式隱含繼承自**system:: object**類別。 在.NET 中，而不是在 Visual c + + 語法中所描述的一部分，屬性會顯示為基礎的資料成員存取的 get/set 函式。 Get/set 函式會出現在這份清單中，做為一般方法。 不是由 Visual c + + 編譯器透過 common language runtime 支援反映。

雖然您可以使用此程式碼來檢查您定義的組件，您也可以使用此程式碼來檢查.NET 組件。 例如，如果您變更 TestAssembly mscorlib 時，您會看到每個型別和方法在 mscorlib.dll 中定義的清單。

```cpp
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

## <a name="see-also"></a>另請參閱

- [以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
