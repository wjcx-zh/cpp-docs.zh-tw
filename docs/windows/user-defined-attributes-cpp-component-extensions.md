---
title: 使用者定義的屬性 (C + + /cli 和 C + + /CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- metadata, extending
- custom attributes, extending metadata
ms.assetid: 98b29048-a3ea-4698-8441-f149cdaec9fb
ms.openlocfilehash: f64cf5415e79678f0e0b43b58aae2249601fb3d7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50546649"
---
# <a name="user-defined-attributes--ccli-and-ccx"></a>使用者定義的屬性 (C + + /cli 和 C + + /CX)

C + + /cli 和 C + + /CX 可讓您建立擴充的介面、 類別或結構、 方法、 參數或列舉型別中繼資料的平台特定屬性。 這些屬性是區別[標準 c + + 屬性](../cpp/attributes.md)。

## <a name="windows-runtime"></a>Windows 執行階段

您可以套用 C + + /CX 屬性至屬性，但不適用於建構函式或方法。

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

本主題所述的語法與資訊要取代所顯示的資訊[屬性](attributes/attribute.md)。

您可以定義自訂屬性型別定義，並讓<xref:System.Attribute>基底類別類型，並選擇性地套用<xref:System.AttributeUsageAttribute>屬性。

如需詳細資訊，請參閱:

- [屬性目標](attribute-targets-cpp-component-extensions.md)

- [屬性參數類型](attribute-parameter-types-cpp-component-extensions.md)

如需 Visual c + + 中簽署組件資訊，請參閱[強式名稱組件 （組件簽署） (C + + /cli CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)。

### <a name="requirements"></a>需求

編譯器選項：`/clr`

### <a name="examples"></a>範例

下列範例示範如何定義自訂屬性。

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

下列範例會說明一些重要功能的自訂屬性。 比方說，此範例中顯示的自訂屬性的常見用法： 具現化的完整用戶端描述自己的伺服器。

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

`Object^`類型會取代 variant 資料類型。 下列範例會定義自訂屬性，以接受陣列`Object^`做為參數。

屬性引數必須是編譯時期常數;在大部分情況下，它們應該是常數常值。

請參閱[typeid](typeid-cpp-component-extensions.md)如需有關如何從自訂屬性區塊中傳回值為 system:: type 資訊。

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

執行階段需要自訂屬性類別的公開部分必須是可序列化。  撰寫自訂的屬性時，您的自訂屬性的具名引數會受限於使用編譯時間常數。  （將它視為一串附加至您的類別配置，中繼資料中的位元。）

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

[適用於.NET 和 UWP 的元件擴充功能](component-extensions-for-runtime-platforms.md)