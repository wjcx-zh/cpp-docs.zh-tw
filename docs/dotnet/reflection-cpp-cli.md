---
title: 反映 (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- typeid keyword [C++]
- reflection [C++}, about reflection
- metadata, reflection
- GetType method
- .NET Framework [C++], reflection
- data types [C++], reflection
- reflection [C++}
- plug-ins [C++]
- reflection [C++}, plug-ins
- assemblies [C++], enumerating data types in
- public types [C++]
- reflection [C++], external assemblies
- assemblies [C++]
- data types [C++], enumerating
- public members [C++]
ms.assetid: 46b6ff4a-e441-4022-8892-78e69422f230
ms.openlocfilehash: 769ba87f64a8096ac8c7f14cc091119345177b3b
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57426442"
---
# <a name="reflection-ccli"></a>反映 (C++/CLI)

反映可讓您在執行階段檢查已知的資料類型。 反映可讓資料類型的列舉中指定的組件，並可以探索到指定的類別或實值類型的成員。 這是不論是否已知或在編譯時期參考的類型，則為 true。 這可讓反映實用的功能進行開發和程式碼管理工具。

請注意，所提供的組件名稱的強式名稱 (請參閱[建立和使用強式名稱組件](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies))，包括組件版本、 文化特性，以及簽章的資訊。 也請注意，在其中定義資料類型的命名空間的名稱可以擷取，以及基底類別的名稱。

若要存取反映功能的最常見方式是透過<xref:System.Object.GetType%2A>方法。 這個方法藉由提供<xref:System.Object?displayProperty=nameWithType>，從衍生所有記憶體回收的類別。

> [!NOTE]
> 如果.exe 已內建只允許上使用 Visual c + + 編譯器建置的.exe 的反映 **/clr: pure**或 **/clr: safe**編譯器選項。 **/Clr: pure**並 **/clr: safe**編譯器選項為已被取代，在 Visual Studio 2015 和 Visual Studio 2017 中無法使用。 請參閱[/clr （Common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md)如需詳細資訊。

如需詳細資訊，請參閱<xref:System.Reflection>。

## <a name="example-gettype"></a>範例：GetType

`GetType`方法傳回的指標<xref:System.Type>類別的物件，其中描述在當物件為基礎的型別。 (**型別**物件不包含任何執行個體的特定資訊。)一個這類項目是型別，可以顯示，如下所示的完整名稱：

請注意類型名稱包含類型定義所在，包括命名空間的完整範圍，而且它會顯示在.NET 的語法，加上範圍解析運算子為一個點。

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

實值型別可以搭配`GetType`函式，但它們必須先將它 boxed。

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

如同`GetType`方法中， [typeid](../windows/typeid-cpp-component-extensions.md)運算子會傳回的指標**類型**物件，因此這個代碼表示的型別名稱**System.Int32**。 顯示型別名稱是反映的最基本功能，但可能更有用的技巧是要檢查或探索有效的列舉型別值。 做法是使用靜態**enum:: getnames**函式，它會傳回字串陣列，每一個都包含文字格式的列舉值。  下列範例會擷取描述的值列舉值的字串陣列**選項**(CLR) 列舉，並在迴圈中顯示它們。

如果是第四個選項新增至**選項**列舉型別，此程式碼會報告新的選項，而不必重新編譯，即使在不同的組件中已定義列舉。

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

## <a name="example-gettype-members-and-properties"></a>範例：GetType 成員和屬性

`GetType`物件支援的成員和屬性，可用來檢查類型。 此程式碼會擷取並顯示某幾項資訊：

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

反映也可讓組件內的型別和類別成員的列舉型別。 若要示範這項功能，定義一個簡單的類別：

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

如果上述程式碼編譯成 DLL，稱為 vcpp_reflection_6.dll 時，您接著可以使用反映來檢查此組件的內容。 這牽涉到使用靜態的反映 API 函式 xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType 來載入組件。 此函式傳回的位址**組件**接著可以查詢有關模組和類型內的物件。

一旦反映系統成功載入的組件的陣列**型別**物件擷取<xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType>函式。 雖然只有一個類別定義在此情況下，每個陣列元素會包含不同類型的相關資訊。 使用迴圈，每個**型別**此陣列中查詢使用的型別成員相關**Type::GetMembers**函式。 此函式傳回的陣列**MethodInfo**物件、 每個物件，包含成員函式、 資料成員或類型中的屬性的相關資訊。

中的附註的方法清單包括函式明確地定義**TestClass**及函式會隱含地繼承自**system:: object**類別。 在.NET 中，而不是在 Visual c + + 語法中所描述的一部分，屬性會顯示為基礎的資料成員存取的 get/set 函式。 Get/set 函式出現在此清單做為一般方法。 透過 common language runtime 中，不是由 Visual c + + 編譯器支援反映。

雖然您可以使用此程式碼來檢查您所定義的組件，您也可以使用此程式碼來檢查.NET 組件。 例如，如果您變更 TestAssembly mscorlib 時，您會看到每個型別和 mscorlib.dll 中定義的方法清單。

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

## <a name="implement"></a>如何：實作使用反映外掛程式元件架構

下列程式碼範例示範如何使用反映來實作簡單的 「 外掛程式 」 架構。 第一個清單應用程式，而第二個外掛程式。 應用程式是填入本身使用任何以 form 為基礎的類別做為命令列引數所提供的外掛程式 DLL 中找到的多個文件表單。

應用程式嘗試載入使用提供的組件<xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName>方法。 如果成功，組件內的型別列舉使用<xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=fullName>方法。 每個型別接著檢查相容性使用<xref:System.Type.IsAssignableFrom%2A?displayProperty=fullName>方法。 在此範例中，提供的組件中找到的類別必須衍生自<xref:System.Windows.Forms.Form>近似於外掛程式類別。

相容的類別會接著使用具現化<xref:System.Activator.CreateInstance%2A?displayProperty=fullName>方法，它接受<xref:System.Type>做為引數和傳回的新執行個體的指標。 然後附加到表單，顯示每個新的執行個體。

請注意，<xref:System.Reflection.Assembly.Load%2A>方法不接受包含副檔名的組件名稱。 因此下列程式碼範例適用於在任一情況下，應用程式中的 main 函式會修剪任何提供的延伸模組。

### <a name="example"></a>範例

下列程式碼會定義接受外掛程式的應用程式。必須提供組件名稱做為第一個引數。 這個組件應該包含至少一個公用<xref:System.Windows.Forms.Form>衍生型別。

```cpp
// plugin_application.cpp
// compile with: /clr /c
#using <system.dll>
#using <system.drawing.dll>
#using <system.windows.forms.dll>

using namespace System;
using namespace System::Windows::Forms;
using namespace System::Reflection;

ref class PluggableForm : public Form  {
public:
   PluggableForm() {}
   PluggableForm(Assembly^ plugAssembly) {
      Text = "plug-in example";
      Size = Drawing::Size(400, 400);
      IsMdiContainer = true;

      array<Type^>^ types = plugAssembly->GetTypes( );
      Type^ formType = Form::typeid;

      for (int i = 0 ; i < types->Length ; i++) {
         if (formType->IsAssignableFrom(types[i])) {
            // Create an instance given the type description.
            Form^ f = dynamic_cast<Form^> (Activator::CreateInstance(types[i]));
            if (f) {
               f->Text = types[i]->ToString();
               f->MdiParent = this;
               f->Show();
            }
         }
      }
   }
};

int main() {
   Assembly^ a = Assembly::LoadFrom("plugin_application.exe");
   Application::Run(gcnew PluggableForm(a));
}
```

### <a name="example"></a>範例

下列程式碼會定義三個類別衍生自<xref:System.Windows.Forms.Form>。 時產生的組件名稱傳遞至先前的清單中的可執行檔，每個三個類別將可探索和具現化，儘管它們是裝載的應用程式，在編譯時期未知。

```cpp
// plugin_assembly.cpp
// compile with: /clr /LD
#using <system.dll>
#using <system.drawing.dll>
#using <system.windows.forms.dll>

using namespace System;
using namespace System::Windows::Forms;
using namespace System::Reflection;
using namespace System::Drawing;

public ref class BlueForm : public Form {
public:
   BlueForm() {
      BackColor = Color::Blue;
   }
};

public ref class CircleForm : public Form {
protected:
   virtual void OnPaint(PaintEventArgs^ args) override {
      args->Graphics->FillEllipse(Brushes::Green, ClientRectangle);
   }
};

public ref class StarburstForm : public Form {
public:
   StarburstForm(){
      BackColor = Color::Black;
   }
protected:
   virtual void OnPaint(PaintEventArgs^ args) override {
      Pen^ p = gcnew Pen(Color::Red, 2);
      Random^ r = gcnew Random( );
      Int32 w = ClientSize.Width;
      Int32 h = ClientSize.Height;
      for (int i=0; i<100; i++) {
         float x1 = w / 2;
         float y1 = h / 2;
         float x2 = r->Next(w);
         float y2 = r->Next(h);
         args->Graphics->DrawLine(p, x1, y1, x2, y2);
      }
   }
};
```

## <a name="enumerate"></a>如何：列舉使用反映的組件中的資料類型

下列程式碼示範的公用類型和成員使用列舉<xref:System.Reflection>。

指定組件的名稱之後的本機目錄中或在 GAC 中，下列程式碼會嘗試開啟組件，並擷取描述。 如果成功的話，每個類型會顯示其公用成員。

請注意，<xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName>要求使用的不具副檔名。 因此，使用 「 mscorlib.dll"作為命令列引數時將會失敗，使用只是 「 mscorlib"會產生.NET Framework 類型的顯示。 如果不提供任何組件名稱，程式碼會偵測並報告目前的組件中的類型 (此程式碼所產生的 EXE)。

### <a name="example"></a>範例

```cpp
// self_reflection.cpp
// compile with: /clr
using namespace System;
using namespace System::Reflection;
using namespace System::Collections;

public ref class ExampleType {
public:
   ExampleType() {}
   void Func() {}
};

int main() {
   String^ delimStr = " ";
   array<Char>^ delimiter = delimStr->ToCharArray( );
   array<String^>^ args = Environment::CommandLine->Split( delimiter );

// replace "self_reflection.exe" with an assembly from either the local
// directory or the GAC
   Assembly^ a = Assembly::LoadFrom("self_reflection.exe");
   Console::WriteLine(a);

   int count = 0;
   array<Type^>^ types = a->GetTypes();
   IEnumerator^ typeIter = types->GetEnumerator();

   while ( typeIter->MoveNext() ) {
      Type^ t = dynamic_cast<Type^>(typeIter->Current);
      Console::WriteLine("   {0}", t->ToString());

      array<MemberInfo^>^ members = t->GetMembers();
      IEnumerator^ memberIter = members->GetEnumerator();
      while ( memberIter->MoveNext() ) {
         MemberInfo^ mi = dynamic_cast<MemberInfo^>(memberIter->Current);
         Console::Write("      {0}", mi->ToString( ) );
         if (mi->MemberType == MemberTypes::Constructor)
            Console::Write("   (constructor)");

         Console::WriteLine();
      }
      count++;
   }
   Console::WriteLine("{0} types found", count);
}
```

## <a name="see-also"></a>另請參閱

- [以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
