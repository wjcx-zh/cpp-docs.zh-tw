---
title: Friend 組件 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- friend assemblies, Visual C++
ms.assetid: 8d55fee0-b7c2-4fbe-a23b-dfe424dc71cd
ms.openlocfilehash: a42caaf07f6ec0c71f63d6a0df8a79fff6f737e6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221441"
---
# <a name="friend-assemblies-c"></a>Friend 組件 (C++)

針對適用的執行時間， *friend*元件語言功能可讓元件元件中的命名空間範圍或全域範圍內的類型，可供一或多個用戶端元件或. .netmodule 存取。

## <a name="all-runtimes"></a>所有執行階段

**備註**

(不是所有執行階段都有支援這個語言功能)。

## <a name="windows-runtime"></a>Windows 執行階段

**備註**

(Windows 執行階段不支援這個語言功能。)

### <a name="requirements"></a>需求

編譯器選項： **/ZW**

## <a name="common-language-runtime"></a>Common Language Runtime

**備註**

#### <a name="to-make-types-at-namespace-scope-or-global-scope-in-an-assembly-component-accessible-to-a-client-assembly-or-netmodule"></a>讓組件元件中在命名空間範圍或全域範圍的類型可存取用戶端組件或 .netmodule

1. 在元件中，指定組件屬性 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>，並傳遞將存取元件中在命名空間範圍或全域範圍之類型的用戶端組件或 .netmodule 的名稱。  您可以藉由指定其他屬性來指定多個用戶端組件或 .netmodule。

1. 在用戶端元件或. .netmodule 中，當您使用來參考元件元件時， `#using` 請傳遞 **`as_friend`** 屬性。  如果您為 **`as_friend`** 未指定的元件指定屬性 `InternalsVisibleToAttribute` ，則會在您嘗試存取元件中命名空間範圍或全域範圍的類型時，擲回執行時間例外狀況。

如果包含屬性的元件沒有 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 強式名稱，但使用該屬性的用戶端元件執行了，就會產生組建錯誤 **`as_friend`** 。

雖然在命名空間範圍和全域範圍的類型可以讓用戶端組件或 .netmodule 知道，成員存取範圍仍然有效。  例如，您無法存取私人成員。

必須明確授與組件中所有類型的存取權。  例如，如果組件 C 參考組件 B，而組件 B 具有組件 A 中所有類型的存取權，則組件 C 沒有組件 A 中所有類型的存取權。

如需如何簽署（也就是如何提供強式名稱）（使用 Microsoft c + + 編譯器建立的元件）的相關資訊，請參閱[強式名稱元件（元件簽署）（c + +/cli）](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)。

對於使用 friend 組件功能的替代方案，您可以使用 <xref:System.Security.Permissions.StrongNameIdentityPermission> 限制對個別類型的存取。

### <a name="requirements"></a>需求

編譯器選項： **/clr**

### <a name="examples"></a>範例

下列程式碼範例會定義可指定具有元件類型存取權之用戶端組件的元件。

```cpp
// friend_assemblies.cpp
// compile by using: /clr /LD
using namespace System::Runtime::CompilerServices;
using namespace System;
// an assembly attribute, not bound to a type
[assembly:InternalsVisibleTo("friend_assemblies_2")];

ref class Class1 {
public:
   void Test_Public() {
      Console::WriteLine("Class1::Test_Public");
   }
};
```

下一個程式碼範例會存取元件中的私用類型。

```cpp
// friend_assemblies_2.cpp
// compile by using: /clr
#using "friend_assemblies.dll" as_friend

int main() {
   Class1 ^ a = gcnew Class1;
   a->Test_Public();
}
```

```Output
Class1::Test_Public
```

下一個程式碼範例會定義元件，但不指定具有元件中各類型之存取權的用戶端組件。

請注意，元件是使用 **/opt： noref**所連結。 這可確保私用類型在元件的中繼資料中發出，當 `InternalsVisibleTo` 屬性存在時則不需要。 如需詳細資訊，請參閱[/opt （優化）](../build/reference/opt-optimizations.md)。

```cpp
// friend_assemblies_3.cpp
// compile by using: /clr /LD /link /opt:noref
using namespace System;

ref class Class1 {
public:
   void Test_Public() {
      Console::WriteLine("Class1::Test_Public");
   }
};
```

下列程式碼範例會定義嘗試存取元件中私用類型 (其未將存取權授與其私用類型) 的用戶端。 由於執行階段的行為，如果您要攔截例外狀況，您必須嘗試存取在 helper 函式的私用類型。

```cpp
// friend_assemblies_4.cpp
// compile by using: /clr
#using "friend_assemblies_3.dll" as_friend
using namespace System;

void Test() {
   Class1 ^ a = gcnew Class1;
}

int main() {
   // to catch this kind of exception, use a helper function
   try {
      Test();
   }
   catch(MethodAccessException ^ e) {
      Console::WriteLine("caught an exception");
   }
}
```

```Output
caught an exception
```

下一個程式碼範例顯示如何建立可指定具有元件類型存取權之用戶端組件的強式名稱元件。

```cpp
// friend_assemblies_5.cpp
// compile by using: /clr /LD /link /keyfile:friend_assemblies.snk
using namespace System::Runtime::CompilerServices;
using namespace System;
// an assembly attribute, not bound to a type

[assembly:InternalsVisibleTo("friend_assemblies_6, PublicKey=00240000048000009400000006020000002400005253413100040000010001000bf45d77fd991f3bff0ef51af48a12d35699e04616f27ba561195a69ebd3449c345389dc9603d65be8cd1987bc7ea48bdda35ac7d57d3d82c666b7fc1a5b79836d139ef0ac8c4e715434211660f481612771a9f7059b9b742c3d8af00e01716ed4b872e6f1be0e94863eb5745224f0deaba5b137624d7049b6f2d87fba639fc5")];

private ref class Class1 {
public:
   void Test_Public() {
      Console::WriteLine("Class1::Test_Public");
   }
};
```

請注意，該元件必須指定其公開金鑰。 建議您依序在命令提示字元執行下列命令，以建立金鑰組，並取得公開金鑰：

**sn-d friend_assemblies .snk**

**sn-k friend_assemblies .snk**

**sn-i friend_assemblies .snk friend_assemblies .snk**

**sn-pc friend_assemblies .snk 金鑰. publickey**

**sn -tp key.publickey**

下一個程式碼範例會存取在強式名稱元件中的私用類型。

```cpp
// friend_assemblies_6.cpp
// compile by using: /clr /link /keyfile:friend_assemblies.snk
#using "friend_assemblies_5.dll" as_friend

int main() {
   Class1 ^ a = gcnew Class1;
   a->Test_Public();
}
```

```Output
Class1::Test_Public
```

## <a name="see-also"></a>另請參閱

[執行階段平台的元件延伸模組](../extensions/component-extensions-for-runtime-platforms.md)
