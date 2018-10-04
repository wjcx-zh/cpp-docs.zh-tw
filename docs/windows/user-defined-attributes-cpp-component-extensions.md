---
title: 使用者定義的屬性 （c + + 元件延伸模組） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- metadata, extending
- custom attributes, extending metadata
ms.assetid: 98b29048-a3ea-4698-8441-f149cdaec9fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3c2f5568b067c119bfa65744290c39d7ca577072
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789224"
---
# <a name="user-defined-attributes--c-component-extensions"></a>使用者定義屬性 (C++ 元件擴充功能)

自訂屬性可讓您擴充的介面、 類別或結構、 方法、 參數或列舉型別中繼資料。

## <a name="all-runtimes"></a>所有執行階段

所有執行階段支援的自訂屬性。

## <a name="windows-runtime"></a>Windows 執行階段

C + + /CX 屬性支援只有屬性，但不是屬性建構函式或方法。

### <a name="remarks"></a>備註

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

自訂屬性，可讓您擴充的受管理的項目中繼資料。 如需詳細資訊，請參閱[屬性](/dotnet/standard/attributes/index)。

### <a name="remarks"></a>備註

本主題所述的語法與資訊要取代所顯示的資訊[屬性](attributes/attribute.md)。

您可以定義自訂屬性型別定義，並讓<xref:System.Attribute>基底類別類型，並選擇性地套用<xref:System.AttributeUsageAttribute>屬性。

比方說，在 Microsoft Transaction Server (MTS) 1.0 時，同步處理的交易而言，行為的負載平衡，並透過自訂插入使用 ODL 自訂屬性的型別程式庫的 Guid 指定等等。 因此，MTS 伺服器的用戶端無法讀取類型程式庫來判斷其特性。 在.NET Framework 中，型別程式庫的類比中繼資料，而類比 ODL 自訂屬性的自訂屬性。 此外，讀取類型程式庫是類似於使用反映的類型。

如需詳細資訊，請參閱：

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

[執行階段平台的元件延伸模組](component-extensions-for-runtime-platforms.md)