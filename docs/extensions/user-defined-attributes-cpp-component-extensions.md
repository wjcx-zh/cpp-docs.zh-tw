---
title: 使用者定義屬性  (C++/CLI 和 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- metadata, extending
- custom attributes, extending metadata
ms.assetid: 98b29048-a3ea-4698-8441-f149cdaec9fb
ms.openlocfilehash: aed36ac7fed7eb1f16f8648f7bcd7efb37f43a75
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171888"
---
# <a name="user-defined-attributes--ccli-and-ccx"></a>使用者定義屬性  (C++/CLI 和 C++/CX)

C++/ CLI 和 C++/CX 可讓您建立能擴充介面、類別或結構、方法、參數，或列舉之中繼資料的平台特定屬性。 這些屬性不同於[標準 C++ 屬性](../cpp/attributes.md)。

## <a name="windows-runtime"></a>Windows 執行階段

您可以將 C++/CX 屬性套用至摘要資訊，但不能套用至建構函式或方法。

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

本主題描述的資訊和語法是要用於取代[屬性](../windows/attributes/attribute.md)中提供的資訊。

您可以透過定義類型並將 <xref:System.Attribute> 作為類型的基底類別，以及選擇性套用 <xref:System.AttributeUsageAttribute> 屬性，以定義自訂屬性。

如需詳細資訊，請參閱

- [屬性目標](attribute-targets-cpp-component-extensions.md)

- [屬性參數類型](attribute-parameter-types-cpp-component-extensions.md)

如需在 Visual C++ 中簽署組件的資訊，請參閱[強式名稱組件 (組件簽署) (C++/CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)。

### <a name="requirements"></a>需求

編譯器選項：`/clr`

### <a name="examples"></a>範例

以下範例示範如何定義自訂屬性。

```cpp
// user_defined_attributes.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::All)]
ref struct Attr : public Attribute {
   Attr(bool i){}
   Attr(){}
};

[Attr]
ref class MyClass {};
```

以下範例說明自訂屬性的一些重要功能。 例如，此範例示範自訂屬性的常見用法：將可向用戶端完整描述自己的伺服器具現化。

```cpp
// extending_metadata_b.cpp
// compile with: /clr
using namespace System;
using namespace System::Reflection;

public enum class Access { Read, Write, Execute };

// Defining the Job attribute:
[AttributeUsage(AttributeTargets::Class, AllowMultiple=true )]
public ref class Job : Attribute {
public:
   property int Priority {
      void set( int value ) { m_Priority = value; }
      int get() { return m_Priority; }
   }

   // You can overload constructors to specify Job attribute in different ways
   Job() { m_Access = Access::Read; }
   Job( Access a ) { m_Access = a; }
   Access m_Access;

protected:
   int m_Priority;
};

interface struct IService {
   void Run();
};

   // Using the Job attribute:
   // Here we specify that QueryService is to be read only with a priority of 2.
   // To prevent namespace collisions, all custom attributes implicitly
   // end with "Attribute".

[Job( Access::Read, Priority=2 )]
ref struct QueryService : public IService {
   virtual void Run() {}
};

// Because we said AllowMultiple=true, we can add multiple attributes
[Job(Access::Read, Priority=1)]
[Job(Access::Write, Priority=3)]
ref struct StatsGenerator : public IService {
   virtual void Run( ) {}
};

int main() {
   IService ^ pIS;
   QueryService ^ pQS = gcnew QueryService;
   StatsGenerator ^ pSG = gcnew StatsGenerator;

   //  use QueryService
   pIS = safe_cast<IService ^>( pQS );

   // use StatsGenerator
   pIS = safe_cast<IService ^>( pSG );

   // Reflection
   MemberInfo ^ pMI = pIS->GetType();
   array <Object ^ > ^ pObjs = pMI->GetCustomAttributes(false);

   // We can now quickly and easily view custom attributes for an
   // Object through Reflection */
   for( int i = 0; i < pObjs->Length; i++ ) {
      Console::Write("Service Priority = ");
      Console::WriteLine(static_cast<Job^>(pObjs[i])->Priority);
      Console::Write("Service Access = ");
      Console::WriteLine(static_cast<Job^>(pObjs[i])->m_Access);
   }
}
```

```Output
Service Priority = 0

Service Access = Write

Service Priority = 3

Service Access = Write

Service Priority = 1

Service Access = Read
```

`Object^` 類型可取代變化資料類型。 以下範例可定義接受 `Object^` 的陣列作為參數的自訂屬性。

屬性引數必須是編譯時間常數；在大部分情況下，它們應該是常數常值。

請參閱 [typeid](typeid-cpp-component-extensions.md) 取得相關資訊，了解如何從自訂屬性區塊傳回 System::Type 的值。

```cpp
// extending_metadata_e.cpp
// compile with: /clr /c
using namespace System;
[AttributeUsage(AttributeTargets::Class | AttributeTargets::Method)]
public ref class AnotherAttr : public Attribute {
public:
   AnotherAttr(array<Object^>^) {}
   array<Object^>^ var1;
};

// applying the attribute
[ AnotherAttr( gcnew array<Object ^> { 3.14159, "pi" }, var1 = gcnew array<Object ^> { "a", "b" } ) ]
public ref class SomeClass {};
```

執行階段要求自訂屬性類別的公開部分必須是可序列化的。  撰寫自訂屬性時，其具名引數僅限使用編譯時間常數。  (請將它視為中繼資料中附加至您類別配置的位元序列。)

```cpp
// extending_metadata_f.cpp
// compile with: /clr /c
using namespace System;
ref struct abc {};

[AttributeUsage( AttributeTargets::All )]
ref struct A : Attribute {
   A( Type^ ) {}
   A( String ^ ) {}
   A( int ) {}
};

[A( abc::typeid )]
ref struct B {};
```

## <a name="see-also"></a>另請參閱

[適用於.NET 和 UWP 的元件延伸模組](component-extensions-for-runtime-platforms.md)
